# 🏢 Active Directory Labs

![Active Directory](https://img.shields.io/badge/Active%20Directory-Domain%20Services-0078D6)
![Windows Server 2022](https://img.shields.io/badge/Windows%20Server-2022-00A4EF)
![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-blue)
![Sysmon](https://img.shields.io/badge/Sysmon-Endpoint-orange)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red)

## Overview

This section documents the Active Directory extension of my cybersecurity home lab — built to simulate realistic AD attack techniques and develop detection engineering skills against a real domain environment, since AD-related attacks (Kerberoasting, credential theft, lateral movement) make up a large share of real-world SOC alert volume.

The environment was built from scratch on top of the existing home lab (see [Home-Lab-Setup](../Home-Lab-Setup/)).

---

## Lab Topology

| Component | Detail | IP Address |
|-----------|--------|------------|
| Domain Controller | Windows Server 2022 (DC01), domain `corp.local` | 192.168.56.60 |
| Domain-Joined Client | Windows 11 Enterprise | 192.168.56.70 |
| SIEM | Wazuh Server | 192.168.56.50 |
| Attacker Machine | Kali Linux | 192.168.56.20 |

All machines run on a dual-adapter configuration (NAT for internet access + Host-Only "labnet" network for isolated lab traffic).

---

## Accounts & Objects

| Object | Purpose |
|--------|---------|
| `Testuser` | Standard domain account used for authentication testing and Kerberoasting simulations |
| `svc-sql` | Service account with SPN `MSSQLSvc/dc01.corp.local:1433` — configured as the Kerberoasting target |

---

## Endpoint Telemetry

Sysmon was deployed on both DC01 and the domain-joined Windows 11 client using **Olaf Hartong's sysmon-modular config (schema 4.90)**.

An earlier custom Sysmon configuration caused repeated service crashes on DC01. Root cause: incorrect `WmiEvent` RuleGroup schema nesting. Switching to the modular config resolved this and became the standard config across both Windows endpoints.

---

## Build & Troubleshooting Notes

Real issues encountered and resolved while standing up this lab:

- **DC01 timezone** was misconfigured and corrected to IST to keep event timestamps aligned with the rest of the lab.
- **DNS misconfiguration**: DC01 was registering its NAT adapter IP instead of its labnet IP in DNS, breaking name resolution for domain-joined clients. Resolved by correcting adapter binding order and re-registering DNS.
- **Wazuh detection gap (Kerberoasting)**: raw Event ID 4769 events were reaching DC01 but rule 100401 wasn't firing in Wazuh. Traced to the event forwarding/rule reload pipeline — see the [Kerberoasting Detection Investigation](../SOC-Investigations/07-Kerberoasting-Detection-Investigation/) for the full root-cause writeup.

---

## Custom Detection Rules

| Rule ID | Purpose |
|---------|---------|
| 100200 / 100201 | Event ID 4769 (Kerberos Service Ticket Request) baseline detection |
| 100400 / 100401 / 100410 | Kerberoasting-specific detection (RC4-encrypted TGS-REQ against SPN accounts) |

---

## Investigations Using This Lab

➡️ **[SOC Investigation #07 — Kerberoasting Detection](../SOC-Investigations/07-Kerberoasting-Detection-Investigation/)**

---

## Skills Demonstrated

- Active Directory deployment and domain configuration
- Service Principal Name (SPN) configuration
- Sysmon deployment and configuration troubleshooting
- Custom Wazuh rule development for Windows Security Event IDs
- Kerberoasting attack simulation and detection engineering
- DNS and adapter-level lab network troubleshooting
- MITRE ATT&CK mapping (T1558.003)

---

## Future Enhancements

- AS-REP Roasting simulation and detection
- Golden Ticket / Silver Ticket attack simulation
- DCSync detection
- Group Policy–based hardening and monitoring
- Additional domain-joined endpoints for lateral movement scenarios

---

This lab serves as the foundation for ongoing Active Directory attack simulation and detection engineering work as the portfolio expands.
