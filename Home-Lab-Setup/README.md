# Cybersecurity Home Lab Setup

## Objective
Built an isolated cybersecurity home lab using VirtualBox for penetration testing, networking practice, packet analysis, and SOC learning.

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Kali Linux | Attacker Machine | 192.168.56.20 |
| Metasploitable 2 | Vulnerable Target | 192.168.56.10 |
| Ubuntu | Linux Practice Machine | 192.168.56.30 |
| Windows 11 | SOC/Windows Analysis | 192.168.56.40 |

---

# Technologies Used

- VirtualBox
- Kali Linux
- Metasploitable 2
- Ubuntu
- Windows 11
- Internal Networking
- ICMP
- Linux Networking Commands

---

# Network Configuration

All virtual machines were configured using Internal Network mode inside VirtualBox to safely isolate the lab environment from the internet.

---

# Connectivity Verification

Connectivity between machines was verified using ICMP ping tests.

Example:

```bash
ping 192.168.56.10
```

---

# Skills Practiced

- Virtualization
- VM Configuration
- Internal Networking
- Linux Administration
- Basic Troubleshooting
- Network Connectivity Testing

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

## Metasploitable IP Configuration

![Metasploitable IP](lab-screenshots/metasploitable-ip-config.png)

---

# Future Improvements

- Perform Nmap scanning
- Practice Wireshark packet analysis
- Add vulnerability scanning
- Build SOC investigation projects
- Analyze Linux and Windows logs
