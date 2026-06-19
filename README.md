# 🛡️ Cybersecurity Portfolio

<p align="center">

![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Portfolio-blue)
![SOC Analyst](https://img.shields.io/badge/SOC-Analyst-success)
![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-blue)
![Sysmon](https://img.shields.io/badge/Sysmon-Endpoint-orange)
![Windows](https://img.shields.io/badge/Windows-11-0078D6)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Linux-E95420)
![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red)

</p>

---

# 👋 About Me

Hello! I'm **Dinesh Babu**, a Computer Science graduate specializing in Cybersecurity with a strong interest in Security Operations Center (SOC) analysis, threat hunting, endpoint monitoring, and incident investigation.

This repository showcases my hands-on cybersecurity learning journey through practical home lab exercises, networking projects, traffic analysis, and SOC investigations using enterprise security tools.

My goal is to continuously develop real-world defensive security skills while preparing for an entry-level SOC Analyst role.

---

# 🏠 Cybersecurity Home Lab

My practical investigations are performed inside an isolated VirtualBox environment consisting of multiple operating systems and security tools.

```text
                 +----------------------+
                 |    Kali Linux        |
                 |  Attack Simulation   |
                 +----------+-----------+
                            |
                            |
                 +----------v-----------+
                 |   Ubuntu Desktop     |
                 | Linux Endpoint       |
                 +----------+-----------+
                            |
                            |
                 +----------v-----------+
                 | Windows 11 + Sysmon  |
                 | Windows Endpoint     |
                 +----------+-----------+
                            |
                 +----------v-----------+
                 |    Wazuh Agent       |
                 +----------+-----------+
                            |
                 +----------v-----------+
                 |     Wazuh SIEM       |
                 | Detection & Analysis |
                 +----------------------+
```

---

# 📂 Repository Structure

```text
cybersecurity-portfolio
│
├── Home-Lab-Setup
│
├── Network-Scanning
│
├── Wireshark-Traffic-Analysis
│
└── SOC-Investigations
    ├── SSH Authentication Failure Investigation
    ├── Windows Process Investigation
    ├── Linux Privilege Escalation Investigation
    ├── Linux Listening Ports Monitoring
    └── README.md
```

---

# 🛡️ Featured SOC Investigations

| Investigation | Platform | Detection |
|---------------|----------|-----------|
| 🔐 SSH Authentication Failure Investigation | Ubuntu Linux | Multiple failed SSH logins followed by successful authentication |
| 🖥️ Windows Process Investigation | Windows 11 | Sysmon Process Creation (`whoami /priv`) |
| 🔑 Linux Privilege Escalation Investigation | Ubuntu Linux | Successful `sudo` privilege escalation |
| 🌐 Linux Listening Ports Monitoring | Ubuntu Linux | Monitoring changes to listening network ports |

---

# 🌐 Networking Projects

- Network Scanning
- Host Discovery
- Port Scanning
- Service Enumeration
- Network Reconnaissance

---

# 🦈 Traffic Analysis

- Wireshark Packet Analysis
- Protocol Inspection
- Packet Filtering
- Traffic Investigation
- Network Traffic Analysis

---

# 🛠️ Technologies & Tools

### SIEM

- Wazuh

### Endpoint Monitoring

- Sysmon

### Operating Systems

- Windows 11
- Ubuntu Linux
- Kali Linux

### Networking

- Nmap
- Wireshark

### Virtualization

- Oracle VirtualBox

### Security Frameworks

- MITRE ATT&CK

---

# 💼 Skills Demonstrated

- Security Event Investigation
- Threat Hunting
- Windows Security Monitoring
- Linux Security Monitoring
- Authentication Analysis
- Process Creation Analysis
- Privilege Escalation Analysis
- Network Traffic Analysis
- Log Analysis
- Event Correlation
- MITRE ATT&CK Mapping
- Incident Documentation

---

# 📈 Learning Roadmap

## ✅ Completed

- Wazuh SIEM Deployment
- Sysmon Integration
- Windows Endpoint Monitoring
- Linux Endpoint Monitoring
- SSH Authentication Investigation
- Windows Process Investigation
- Linux Privilege Escalation Investigation
- Linux Listening Ports Monitoring
- Wireshark Traffic Analysis
- Network Scanning

## 🚧 In Progress

- Windows Failed Logon Investigation
- Linux User Management Investigation
- File Integrity Monitoring (FIM)
- Nmap Detection Investigation
- Windows PowerShell Investigation
- Advanced Threat Hunting
- Incident Response Scenarios

---

# 🎯 Career Objective

I am actively developing practical SOC Analyst skills through hands-on investigations, security monitoring, and threat hunting using enterprise security tools.

This portfolio demonstrates my ability to simulate, detect, investigate, analyze, and document security events using a structured SOC investigation methodology aligned with industry best practices.

---

# 📬 Connect With Me

- **LinkedIn:** https://www.linkedin.com/in/dinesh-babu-2866a0275
- **GitHub:** https://github.com/Dinesh-kalla

---

⭐ **Thank you for visiting my cybersecurity portfolio!**  
I will continue expanding this repository with additional SOC investigations, threat hunting scenarios, and security projects as I progress in my cybersecurity journey.
