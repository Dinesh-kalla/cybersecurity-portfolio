# 🛡️ SOC Investigations

This section contains hands-on Security Operations Center (SOC) investigations completed within my cybersecurity home lab using Wazuh SIEM, Sysmon, and Linux/Windows security logs.

The investigations progress in complexity — starting with single-host Linux and Windows log analysis, and advancing to multi-host Active Directory attack simulation and detection engineering, reflecting the growing scope of the home lab.

Each investigation follows a structured workflow including:

- Alert validation
- Event analysis
- Threat hunting
- Evidence collection
- MITRE ATT&CK mapping
- Analyst assessment
- Recommendations
- Documentation

---

## 📊 Quick Stats

| Metric | Count |
|--------|-------|
| Total Investigations | 7 |
| Custom Wazuh Detection Rules Written | 6 |
| MITRE ATT&CK Techniques Covered | 4 |
| Platforms Covered | Linux, Windows 11, Windows Server 2022 (AD) |

---

## 🆕 Latest Addition

**🎫 Kerberoasting Detection Investigation** — the most technically advanced investigation to date, built on a full Active Directory lab (domain controller, domain-joined client, service account with SPN). Detects RC4-encrypted Kerberos service ticket requests (Event ID 4769) indicative of a Kerberoasting attempt, mapped to MITRE T1558.003.

[View full investigation →](./07-Kerberoasting-Detection-Investigation/)

---

## Investigation Portfolio

| Investigation | Platform | Detection | Status |
|---------------|----------|-----------|--------|
| 🔐 SSH Authentication Failure Investigation | Ubuntu | Multiple failed SSH logins followed by successful authentication | ✅ Completed |
| 🖥️ Windows Process Investigation | Windows 11 | Sysmon Process Creation (whoami /priv) | ✅ Completed |
| 🔑 Linux Privilege Escalation Investigation | Ubuntu | Successful sudo to ROOT | ✅ Completed |
| 🌐 Linux Listening Ports Monitoring | Ubuntu | Netstat listening ports status changed | ✅ Completed |
| 👤 Linux User Account Creation Investigation | Ubuntu | New local user/group creation via `useradd` (MITRE T1136.001) | ✅ Completed |
| 🔎 Nmap SSH Service Detection Investigation | Ubuntu | Custom Wazuh rule detecting Nmap SSH service scans (MITRE T1595, T1046) | ✅ Completed |
| 🎫 [Kerberoasting Detection Investigation](./07-Kerberoasting-Detection-Investigation/) | Windows Server 2022 (Active Directory) | Custom Wazuh rule detecting RC4-encrypted TGS-REQ (Event ID 4769) for service account SPN (MITRE T1558.003) | ✅ Completed |

---

## Skills Demonstrated

- Security Event Investigation
- Threat Hunting
- Wazuh SIEM
- Sysmon
- Linux Security Monitoring
- Windows Security Monitoring
- Active Directory Security Monitoring
- Authentication Analysis
- Process Creation Analysis
- Privilege Escalation Analysis
- Network Service Monitoring
- User/Group Account Monitoring
- Detection Engineering & Custom Rule Development
- MITRE ATT&CK Mapping
- Incident Documentation

---

## Tools Used

- Wazuh SIEM
- Sysmon
- Ubuntu Linux
- Windows 11
- Windows Server 2022 (Active Directory)
- Kali Linux
- VirtualBox

---

More investigations will be added as my SOC home lab continues to expand.