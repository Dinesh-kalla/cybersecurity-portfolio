# Cybersecurity Home Lab Setup

## Objective

Built an isolated cybersecurity home lab using VirtualBox and Wazuh SIEM for penetration testing, network analysis, endpoint monitoring, threat hunting, and SOC analyst practice.

---

## Lab Infrastructure

| Machine          | Role                  | IP Address    |
| ---------------- | --------------------- | ------------- |
| Kali Linux       | Attacker Machine      | 192.168.56.20 |
| Metasploitable 2 | Vulnerable Target     | 192.168.56.10 |
| Ubuntu Desktop   | Linux Endpoint        | 192.168.56.30 |
| Windows 11       | Windows Endpoint      | 192.168.56.40 |
| Wazuh Server     | SIEM & Log Management | 192.168.56.50 |

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

All virtual machines are connected through an isolated VirtualBox Internal Network to safely perform offensive and defensive cybersecurity exercises without exposing the environment to external systems.

---

## Connectivity Verification

Network communication between lab systems was verified using ICMP ping testing.

Example:

```bash
ping 192.168.56.10
```

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

# Screenshots

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

# Wazuh SIEM Integration

## Objective

Integrated Wazuh SIEM into the home lab to collect endpoint logs, monitor security events, investigate alerts, and perform threat hunting activities.

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

## Wazuh Screenshots

### Wazuh SIEM Overview

![Wazuh SIEM Overview](lab-screenshots/wazuh/wazuh-siem-overview.png)

---

### Active Endpoint Monitoring

![Active Endpoint Monitoring](lab-screenshots/wazuh/active-endpoint-monitoring.png)

---

### Threat Hunting & Event Analysis

![Threat Hunting](lab-screenshots/wazuh/threat-hunting-event-analysis.png)

---

### Wazuh Alert Investigation

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

The event shows the user "admin" successfully executing a sudo command to switch to the root account. Wazuh successfully collected, parsed, and displayed the event for investigation. Such activities should be reviewed in production environments to ensure authorization and compliance.

---

## Key Learnings

* Built and maintained a centralized SIEM environment
* Connected Linux and Windows endpoints to Wazuh
* Investigated real security alerts and events
* Performed threat hunting using collected logs
* Practiced SOC analyst investigation workflows
* Analyzed authentication and endpoint activity logs
* Gained hands-on experience with endpoint security monitoring

---

## Future Enhancements

* Simulate SSH brute-force attacks from Kali Linux
* Investigate attack activity through Wazuh alerts
* Perform MITRE ATT&CK technique mapping
* Create incident response playbooks
* Deploy additional monitored endpoints
* Implement Wazuh Active Response

---

## Portfolio Relevance

This project demonstrates practical experience with:

* Cybersecurity Lab Design
* Network Segmentation
* Endpoint Monitoring
* SIEM Administration
* Threat Hunting
* Alert Investigation
* Security Event Analysis
* SOC Analyst Workflows

The lab serves as a foundation for future incident response, threat detection, and security monitoring projects.

---

## Project Outcome

Successfully designed and deployed a multi-machine cybersecurity home lab consisting of Kali Linux, Metasploitable 2, Ubuntu, Windows 11, and Wazuh SIEM. The environment supports penetration testing, network analysis, endpoint monitoring, threat hunting, alert investigation, and SOC analyst training in a safe isolated network.
