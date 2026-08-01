<h1 align="center">Budget-Friendly SOC Lab</h1>
<h3>Why this lab?</h3>
<br>
<blockquote>
This project demonstrates how to build a functional SOC lab using a single Windows laptop and one Kali Linux VM. The goal is to maximize hands-on learning with limited hardware while exploring endpoint monitoring, detection engineering, and incident investigation using Wazuh.
</blockquote>


![Architecture](images/Lab-Architecture.png)



## Technology Stack

### Infrastructure
- Windows 11 (Wazuh Server Host)
- Windows 11 Endpoint
- VirtualBox

### Security Platform
- Wazuh
- Sysmon
- Wazuh Agent

### Attack Platform
- Kali Linux

---

## Objectives

- Deploy a centralized security monitoring environment
- Configure endpoint telemetry collection
- Simulate attacker techniques
- Detect and analyze security events
- Document attack scenarios and investigations

---

## Repository Structure

wazuh-soc-homelab/
│
├── README.md
├── initial setup/
├── setup/
├── scenarios/
├── images/
├── detections/
└── configs/

---

## Implemented Simulations

- [ ] none

---

### To do's

- [x] initial setup
- [x] agent setup
- [ ] sysmon setup in windows
