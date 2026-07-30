# SOC Investigation #07: Detecting a Kerberoasting Attack with Wazuh SIEM

![Platform](https://img.shields.io/badge/Platform-Windows%20Active%20Directory-blue)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh-green)
![Attack](https://img.shields.io/badge/MITRE-T1558.003-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

# Overview

This project demonstrates the detection and investigation of a **Kerberoasting attack** in a Windows Active Directory environment using **Wazuh SIEM**.

A vulnerable service account (**svc-sql**) was configured with a Service Principal Name (SPN). Using **Rubeus**, a Kerberos service ticket was requested to simulate a Kerberoasting attack. Windows Security Event **4769** was generated, collected by Wazuh, and detected through a **custom Wazuh rule** designed to identify RC4-encrypted Kerberos service ticket requests.

This investigation showcases practical skills in:

- Active Directory Security
- Kerberos Authentication
- SIEM Monitoring
- Detection Engineering
- Windows Event Log Analysis
- MITRE ATT&CK Mapping
- SOC Investigation

---

# Lab Architecture

![Lab Architecture](screenshots/01-Lab-Architecture.png)

---

# Objectives

- Build an Active Directory lab environment.
- Configure a Kerberoastable service account.
- Simulate a Kerberoasting attack using Rubeus.
- Monitor Windows Security events with Wazuh.
- Analyze Event ID 4769.
- Develop a custom Wazuh detection rule.
- Map the attack to the MITRE ATT&CK framework.

---

# Lab Environment

| Component | Details |
|-----------|---------|
| SIEM | Wazuh 4.x |
| Domain Controller | Windows Server 2022 |
| Client | Windows 11 Enterprise |
| Attack Tool | Rubeus v2.3.2 |
| Domain | CORP.LOCAL |
| Service Account | svc-sql |
| SPN | MSSQLSvc/dc01.corp.local:1433 |

---

# Attack Scenario

Kerberoasting is an attack technique where a domain user requests a Kerberos service ticket (TGS) for a service account that has a registered Service Principal Name (SPN). The encrypted ticket can then be extracted and cracked offline to recover the service account password.

During this investigation:

- A service account (**svc-sql**) was configured with an SPN.
- A domain user (**testuser**) requested a service ticket using **Rubeus**.
- Windows generated Security Event **4769**.
- Wazuh collected and analyzed the event.
- A custom rule generated a high-severity alert for potential Kerberoasting activity.

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Credential Access | Kerberoasting | T1558.003 |

---

# Attack Workflow

```text
Domain User (testuser)
        │
        ▼
Rubeus Kerberoast Attack
        │
        ▼
Kerberos TGS Request
        │
        ▼
Windows Security Event 4769
        │
        ▼
Wazuh Agent
        │
        ▼
Wazuh Manager
        │
        ▼
Custom Detection Rule (100401)
        │
        ▼
SOC Investigation
```

---

# Investigation Steps

## Step 1 – Configure the Service Account

A vulnerable service account named **svc-sql** was configured with a Service Principal Name (SPN).

Command:

```powershell
setspn -L svc-sql
```

### Evidence

![SPN Configuration](screenshots/02-SPN-Configuration.png)

---

## Step 2 – Simulate the Kerberoasting Attack

The attack was simulated using **Rubeus**.

Command:

```cmd
Rubeus.exe kerberoast /user:svc-sql
```

The tool successfully requested a Kerberos service ticket and extracted the TGS hash.

### Evidence

![Kerberoast Attack](screenshots/03-Kerberoast-Attack.png)

---

## Step 3 – Windows Event Generation

The Domain Controller generated **Windows Security Event ID 4769**.

Key event information:

| Field | Value |
|--------|-------|
| Event ID | 4769 |
| User | testuser@CORP.LOCAL |
| Service | svc-sql |
| Source IP | 192.168.56.70 |
| Encryption | RC4 (0x17) |

### Evidence

![Windows Event](screenshots/04-EventID-4769.png)

---

## Step 4 – Wazuh Detection

The event was collected by the Wazuh agent and forwarded to the Wazuh Manager.

A custom detection rule identified the activity as a potential Kerberoasting attack.

Alert Details:

| Field | Value |
|--------|-------|
| Rule ID | 100401 |
| Severity | Level 12 |
| MITRE Technique | T1558.003 |
| Description | Possible Kerberoasting: RC4-encrypted Kerberos ticket requested |

### Evidence

![Wazuh Alert](screenshots/05-Wazuh-Alert.png)

---

## Step 5 – Event Analysis

The Wazuh alert was reviewed to validate the attack.

Important indicators included:

- Event ID 4769
- User: **testuser**
- Service Account: **svc-sql**
- Ticket Encryption: **RC4 (0x17)**
- Successful ticket request

### Evidence

![Event Details](screenshots/06-Wazuh-Event-Details.png)

---

## Step 6 – Detection Engineering

To improve visibility into Kerberoasting activity, a custom Wazuh rule was created.

Detection Logic:

- Parent Rule: 100400
- Event ID: 4769
- Ticket Encryption Type: 0x17
- Severity: 12
- MITRE ATT&CK: T1558.003

### Evidence

![Custom Rule](screenshots/07-Custom-Wazuh-Rule.png)

---

# Indicators of Compromise (IOCs)

| Indicator | Value |
|-----------|-------|
| Event ID | 4769 |
| Rule ID | 100401 |
| User | testuser@CORP.LOCAL |
| Service Account | svc-sql |
| Source IP | 192.168.56.70 |
| Ticket Encryption | RC4 (0x17) |

---

# Repository Structure

```text
07-Kerberoasting-Detection-Investigation/
│
├── README.md
│
├── screenshots/
│   ├── 01-Lab-Architecture.png
│   ├── 02-SPN-Configuration.png
│   ├── 03-Kerberoast-Attack.png
│   ├── 04-EventID-4769.png
│   ├── 05-Wazuh-Alert.png
│   ├── 06-Wazuh-Event-Details.png
│   └── 07-Custom-Wazuh-Rule.png
│
├── logs/
│   ├── README.md
│   └── kerberoasting-event-4769.json
│
└── rules/
    ├── README.md
    └── local_active_directory.xml
```

---

# Detection Rule

The custom Wazuh rule detects:

- Windows Security Event ID **4769**
- RC4-encrypted Kerberos service tickets (**0x17**)
- Service ticket requests associated with Kerberoasting activity

The rule generates a **Level 12** alert and maps the activity to **MITRE ATT&CK T1558.003 – Kerberoasting**.

---

# Recommendations

- Use strong, unique passwords for service accounts.
- Replace RC4 encryption with AES where possible.
- Use Group Managed Service Accounts (gMSAs).
- Monitor Event ID 4769 for unusual service ticket activity.
- Audit Service Principal Names (SPNs) regularly.
- Investigate repeated service ticket requests from the same user or endpoint.

---

# Skills Demonstrated

- Active Directory Administration
- Kerberos Authentication
- Attack Simulation
- Windows Event Log Analysis
- Wazuh SIEM
- Detection Engineering
- Threat Hunting
- MITRE ATT&CK Mapping
- SOC Investigation
- Incident Analysis

---

# Evidence

This investigation includes:

- Lab architecture screenshots
- SPN configuration
- Kerberoasting attack execution
- Windows Security Event 4769
- Wazuh alert details
- Custom Wazuh detection rule
- Raw Wazuh JSON alert
- Detection rule source code

---

# Conclusion

This project demonstrates an end-to-end detection workflow for a Kerberoasting attack within an Active Directory environment. A simulated attack generated a Kerberos service ticket request, which was captured as **Windows Security Event ID 4769**, ingested by **Wazuh SIEM**, and successfully detected using a custom detection rule. The investigation highlights practical experience in Active Directory security, Windows event analysis, detection engineering, and SOC investigation methodologies while aligning with the **MITRE ATT&CK** framework.