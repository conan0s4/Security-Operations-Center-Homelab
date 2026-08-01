<h1 align="center">Budget-Friendly SOC Lab</h1>
<h3>Why this lab?</h3>
<br>
<blockquote>
This project demonstrates how to build a functional SOC lab using a single Windows laptop and one Kali Linux VM. The goal is to maximize hands-on learning with limited hardware while exploring endpoint monitoring, detection engineering, and incident investigation using Wazuh.
</blockquote>

---

![Architecture](images/Lab-Architecture.png)

---

## Lab Components

### Main Host
**Operating System**
- Windows 11

**Roles**
- Wazuh Server (Docker)
- Monitored Windows Endpoint (Wazuh Agent)
- VirtualBox Host


### Kali Linux Virtual Machine
**Operating System**
- Kali Linux

**Roles**
- Attack Platform
- Monitored Linux Endpoint (Wazuh Agent)

---

## Objectives

- Deploy a centralized security monitoring environment
- Configure endpoint telemetry collection
- Simulate attacker techniques
- Detect and analyze security events
- Document attack scenarios and investigations

---

## Implemented Simulations

- [ ] none

---

### To do's

- [x] initial setup
- [x] agent setup
- [ ] sysmon setup in windows
