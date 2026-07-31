# 🏠 Home Lab Setup & Wazuh SIEM Integration

![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-blue)
![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94)
![Sysmon](https://img.shields.io/badge/Sysmon-Windows-green)
![Nmap](https://img.shields.io/badge/Nmap-Network%20Scanning-orange)
![Wireshark](https://img.shields.io/badge/Wireshark-Traffic%20Analysis-blue)
![VirtualBox](https://img.shields.io/badge/VirtualBox-Lab-purple)

## Overview

This repository showcases my hands-on cybersecurity projects and practical SOC Analyst learning. It includes a cybersecurity home lab, Wazuh SIEM deployment, network scanning, Wireshark traffic analysis, threat hunting, and security event investigations using industry-standard tools.

---

## 📂 In This Section

* 🏠 Home Lab Infrastructure & Network Architecture
* 🛡️ Wazuh SIEM Integration
* 📸 Screenshots & Evidence
* 🚀 Future Enhancements
* 🏆 Portfolio Relevance & Project Outcome
---

# 🏠 Home Lab Setup

## Lab Infrastructure

| Machine                     | Role                                  | IP Address    |
| --------------------------- | -------------------------------------- | ------------- |
| Kali Linux                  | Attacker Machine                       | 192.168.56.20 |
| Metasploitable 2            | Vulnerable Target                      | 192.168.56.10 |
| Ubuntu Desktop              | Linux Endpoint                         | 192.168.56.30 |
| Wazuh Server                | SIEM & Log Management                  | 192.168.56.50 |
| Windows Server 2022 (DC01)  | Active Directory Domain Controller (corp.local) | 192.168.56.60 |
| Windows 11 Enterprise       | Domain-Joined Windows Endpoint         | 192.168.56.70 |

All machines run on a dual-adapter configuration (NAT for internet access + Host-Only "labnet" network for isolated lab traffic).

---

## Technologies Used

* VirtualBox
* Kali Linux
* Metasploitable 2
* Ubuntu Linux
* Windows 11
* Wazuh SIEM
* Wazuh Agents
* Sysmon
* Nmap
* Wireshark
* TCP/IP Networking
* Internal Network Architecture
* Threat Hunting
* Endpoint Monitoring
* Security Event Analysis

---

## Network Architecture

All virtual machines are connected through an isolated VirtualBox Internal Network, allowing offensive and defensive cybersecurity exercises to be performed safely without exposing the environment to external networks.

---

## Connectivity Verification

Network communication between lab systems was verified using ICMP ping testing.

**Example:**

```bash
ping 192.168.56.10
```

---

---

# 🏢 Active Directory Lab Extension

To support more advanced detection engineering scenarios, the home lab was extended with a Windows Server 2022 domain controller and a domain-joined Windows 11 client.

| Component | Detail |
|-----------|--------|
| Domain Controller | Windows Server 2022 (DC01), domain `corp.local` |
| Domain-Joined Client | Windows 11 Enterprise |
| Test Account | `Testuser`, used for authentication and Kerberoasting simulations |
| Service Account | `svc-sql`, SPN `MSSQLSvc/dc01.corp.local:1433` — Kerberoasting target |
| Endpoint Telemetry | Sysmon deployed on DC01 and the Windows 11 client using Olaf Hartong's sysmon-modular config |

This extension enabled realistic simulation of Active Directory attacks (starting with Kerberoasting) and detection engineering against Event ID 4769 in Wazuh. See [SOC Investigations](../SOC-Investigations/07-Kerberoasting-Detection-Investigation/) for the full writeup.

---

## Skills Practiced

* Virtual Machine Deployment
* Network Configuration
* Internal Network Design
* Linux Administration
* Windows Administration
* Troubleshooting
* Endpoint Monitoring
* Security Monitoring
* Threat Hunting
* Security Event Investigation
* Alert Triage
* SIEM Administration
* SOC Operations
* Log Analysis

---

# 📸 Screenshots

## Kali Linux IP Configuration

![Kali Linux IP](lab-screenshots/kali-linux-ip-config.png)

---

## Successful Ping Test

![Ping Test](lab-screenshots/successful-ping-test.png)

---

## VirtualBox Internal Network Settings

![Internal Network](lab-screenshots/virtualbox-internal-network-settings.png)

---

## Metasploitable 2 IP Configuration

![Metasploitable IP](lab-screenshots/metasploitable-ip-config.png)

---

# 🛡️ Wazuh SIEM Integration

## Overview

Integrated Wazuh SIEM into the home lab to centralize log collection, monitor endpoint activity, investigate security events, and perform threat hunting across Windows and Linux systems.

---

## Wazuh Architecture

| Component     | IP Address    | Purpose                     |
| ------------- | ------------- | --------------------------- |
| Wazuh Server  | 192.168.56.50 | Centralized SIEM Platform   |
| Ubuntu Agent  | 192.168.56.30 | Linux Log Monitoring        |
| Windows Agent | 192.168.56.40 | Windows Security Monitoring |

---

## Features Implemented

* Agent Deployment
* Endpoint Monitoring
* Security Monitoring
* Threat Hunting
* Alert Investigation
* Security Event Collection
* Configuration Assessment
* File Integrity Monitoring
* Log Management

---

# 📊 Wazuh Screenshots

## Wazuh SIEM Overview

![Wazuh SIEM Overview](lab-screenshots/wazuh/wazuh-siem-overview.png)

---

## Active Endpoint Monitoring

![Active Endpoint Monitoring](lab-screenshots/wazuh/active-endpoint-monitoring.png)

---

## Threat Hunting & Event Analysis

![Threat Hunting](lab-screenshots/wazuh/threat-hunting-event-analysis.png)

---

## Wazuh Alert Investigation

![Alert Investigation](lab-screenshots/wazuh/wazuh-alert-investigation.png)

---

## Alert Investigation Summary

| Field            | Value                         |
| ---------------- | ----------------------------- |
| Agent            | Ubuntu                        |
| Source User      | admin                         |
| Target User      | root                          |
| Command Executed | /usr/bin/su                   |
| Detection Source | sudo Logs                     |
| Event Type       | Privilege Escalation Activity |

### Analyst Notes

The event shows the user **admin** successfully executing a **sudo** command to switch to the **root** account. Wazuh collected, parsed, and displayed the event for investigation. Activities involving privilege escalation should always be reviewed in production environments to verify authorization and ensure compliance with security policies.

---

## Key Learnings

* Built and maintained a centralized SIEM environment.
* Connected Windows and Linux endpoints to Wazuh.
* Investigated real security alerts and endpoint events.
* Performed threat hunting using collected telemetry.
* Practiced SOC Analyst investigation workflows.
* Analyzed authentication and endpoint activity logs.
* Gained hands-on experience with endpoint security monitoring.

---

## Future Enhancements

* Simulate SSH brute-force attacks from Kali Linux.
* Investigate attack activity using Wazuh alerts.
* Map detections to the MITRE ATT&CK framework.
* Develop incident response playbooks.
* Deploy additional monitored endpoints.
* Configure and test Wazuh Active Response.

---

## Portfolio Relevance

This project demonstrates practical experience in:

* Cybersecurity Lab Design
* Network Segmentation
* SIEM Administration
* Endpoint Monitoring
* Threat Hunting
* Alert Investigation
* Security Event Analysis
* SOC Analyst Workflows

This home lab serves as the foundation for future detection engineering, incident response, malware analysis, and threat hunting projects.

---

## Project Outcome

Successfully designed and deployed a multi-machine cybersecurity home lab consisting of Kali Linux, Metasploitable 2, Ubuntu Desktop, Windows 11, and Wazuh SIEM. The environment supports penetration testing, network analysis, endpoint monitoring, threat hunting, security event investigation, and practical SOC Analyst training within a safe and isolated network.
