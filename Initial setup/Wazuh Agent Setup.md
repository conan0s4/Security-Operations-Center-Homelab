# Wazuh Agent Setup

---

## Starting the Wazuh Stack

For my home lab, I run Wazuh using Docker Desktop. Before starting the stack, I make sure Docker Desktop is already running.

![Screenshot (134).png](ef5fa550-3587-4a93-b926-4fd5ffcf45eb.png)

The Wazuh Docker files are located at:

```
C:\Users\<username>\wazuh-docker\single-node
```

From that directory, I start the stack using:

```bash
docker compose up -d
```

To stop the stack:

```bash
docker compose down
```

![Screenshot (151).png](6e38197b-a809-45dd-9b17-044ced4d9108.png)

---

# Wazuh Manager (Agent 000)

I did **not** install a Wazuh Agent on the machine hosting the Wazuh Manager.

The manager already monitors its own host as **Agent `000`**, so installing another agent on the same machine is unnecessary.

According to the Wazuh community:

> "The wazuh-manager itself monitors the machine where it is installed, working as an agent, reporting to himself his own alerts as would any other agent do (since it is itself an agent), this agent has the ID 000.
> 
> 
> You can check this with the command `/var/ossec/bin/agent_control -i 000`
> 
> The configuration of each functionality is done in the same way as if it were configured for an agent."
> 

<aside>
💡

Notes:

Agent 000 is an internal agent managed by the Wazuh Manager. It is automatically active while the Wazuh Manager service is running and becomes unavailable when the Wazuh Manager service is stopped.

</aside>

---

# Linux Agent Installation

For my Linux virtual machine, I generated an agent installation command from the Wazuh Dashboard using the following configuration:

| Setting | Value |
| --- | --- |
| Operating System | Linux |
| Package Type | DEB |
| Architecture | AMD64 |
| Server Address | Main host WLAN IP address |
| Agent Name | `LinuxUser02` |

step 1

![Screenshot 2026-08-01 102635.png](Screenshot_2026-08-01_102635.png)

step 2

![Screenshot (137).png](ef622686-6e5f-4011-b50c-5b4acd898f21.png)

step  3

![Screenshot (138).png](Screenshot_(138).png)

step  4

![Screenshot (140).png](77d647a4-1beb-4892-98c2-4820616d11eb.png)

step  5

![Screenshot (141).png](Screenshot_(141).png)

step 6

![Screenshot (143).png](40b7464c-d362-45b4-9b2f-6f442e0f5d2b.png)

Before installing the agent in my linux virtual machine, I switched to the root user since the installation requires root privileges.

```bash
sudo su
```

The generated installation command was:

```bash
wget https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.14.6-1_amd64.deb && WAZUH_MANAGER='<server-addr>' WAZUH_AGENT_NAME='LinuxUser02' dpkg -i ./wazuh-agent_4.14.6-1_amd64.deb
```

![Screenshot (148).png](6f11b1ad-907c-4c21-854e-a808203ce14a.png)

After the installation completed, I enabled and started the agent:

![Screenshot (148).png](b54f6004-4dd6-4b91-afb1-b0e317df8fdd.png)

```bash
systemctl daemon-reload
systemctl enable wazuh-agent
systemctl start wazuh-agent
```

---

# Agent Management

To stop the agent:

```bash
systemctl stop wazuh-agent
```

To start the agent:

```bash
systemctl start wazuh-agent
```

To verify the agent status:

```bash
systemctl status wazuh-agent
```

---

![Screenshot (149).png](Screenshot_(149).png)

The **Endpoint Summary** shows that the Linux agent is **Active**, indicating that the endpoint has been successfully registered with the Wazuh Manager and is operational.

<aside>
💡

At this point, two Wazuh agents are configured: **Agent 000**, which is included by default with the Wazuh Manager, and the Linux agent running on the virtual machine. With both agents operational, the environment is ready for SOC monitoring and attack simulation activities.

</aside>

# References

- [https://www.reddit.com/r/Wazuh/comments/1gk4rxj/can_i_install_wazuh_manager_and_agent_on_the_same/](https://www.reddit.com/r/Wazuh/comments/1gk4rxj/can_i_install_wazuh_manager_and_agent_on_the_same/)
- [https://documentation.wazuh.com/current/user-manual/agent/index.html](https://documentation.wazuh.com/current/user-manual/agent/index.html)
- [https://documentation.wazuh.com/current/user-manual/reference/ossec-conf/index.html](https://documentation.wazuh.com/current/user-manual/reference/ossec-conf/index.html)