# 🛡️ SOC Investigations

This section contains hands-on Security Operations Center (SOC) investigations completed within my cybersecurity home lab using Wazuh SIEM, Sysmon, and Linux security logs.

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

## Investigation Portfolio

| Investigation | Platform | Detection | Status |
|---------------|----------|-----------|--------|
| 🔐 SSH Authentication Failure Investigation | Ubuntu | Multiple failed SSH logins followed by successful authentication | ✅ Completed |
| 🖥️ Windows Process Investigation | Windows 11 | Sysmon Process Creation (whoami /priv) | ✅ Completed |
| 🔑 Linux Privilege Escalation Investigation | Ubuntu | Successful sudo to ROOT | ✅ Completed |
| 🌐 Linux Listening Ports Monitoring | Ubuntu | Netstat listening ports status changed | ✅ Completed |
| 👤 Linux User Account Creation Investigation | Ubuntu | New local user/group creation via `useradd` (MITRE T1136.001) | ✅ Completed |
| 🔎 Nmap SSH Service Detection Investigation | Ubuntu | Custom Wazuh rule detecting Nmap SSH service scans (MITRE T1595, T1046) | ✅ Completed |

---

## Skills Demonstrated

- Security Event Investigation
- Threat Hunting
- Wazuh SIEM
- Sysmon
- Linux Security Monitoring
- Windows Security Monitoring
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
- Kali Linux
- VirtualBox

---

More investigations will be added as my SOC home lab continues to expand.