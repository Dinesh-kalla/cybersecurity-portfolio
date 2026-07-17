# Network Reconnaissance using Nmap

Practical network reconnaissance using **Nmap** to perform host discovery, port scanning, service enumeration, operating system fingerprinting, and vulnerability assessment within an isolated cybersecurity home lab.

---

# Overview

Network reconnaissance is the first phase of nearly every penetration test and cyber attack. Before attempting exploitation, security professionals identify live hosts, enumerate exposed services, fingerprint operating systems, and assess potential vulnerabilities.

This project demonstrates practical Nmap techniques performed against multiple virtual machines in an isolated VirtualBox lab. The objective was to understand how attackers gather information while developing defensive skills in network reconnaissance and security assessment.

---

# Objectives

- Discover active hosts on the network
- Perform TCP Connect and SYN scans
- Identify open TCP ports
- Enumerate running services
- Detect service versions
- Fingerprint operating systems
- Identify known vulnerabilities using the Nmap Scripting Engine (NSE)
- Document findings with screenshots and raw scan evidence

---

# Lab Architecture

```text
                 +----------------------+
                 |     Kali Linux       |
                 |    (Attacker VM)     |
                 +----------+-----------+
                            |
                     Internal Network
                            |
        +-------------------+-------------------+
        |                   |                   |
+-------+------+    +--------+-------+   +------+-------------+
| Ubuntu Desktop|    | Windows 11     |   | Metasploitable 2   |
| Linux Target  |    | Windows Target |   | Vulnerable Target  |
+---------------+    +----------------+   +--------------------+
```

---

# Lab Environment

| Component | Purpose |
|----------|---------|
| Kali Linux | Attacker Machine |
| Ubuntu Desktop | Linux Target |
| Windows 11 | Windows Target |
| Metasploitable 2 | Vulnerable Linux Machine |
| VirtualBox | Virtualization Platform |
| Nmap | Network Reconnaissance Tool |

---

# Tools Used

- Kali Linux
- Nmap
- VirtualBox
- Ubuntu Desktop
- Windows 11
- Metasploitable 2

---

# Labs Performed

---

## Lab 1 – Host Discovery

### Objective

Identify active hosts within the local subnet.

### Command

```bash
nmap -sn 192.168.56.0/24
```

### Description

Performed a ping sweep to discover live hosts without scanning ports.

### Evidence

- Screenshot:
  - `nmap-screenshots/01-host-discovery.png`

- Raw Output:
  - `evidence/host-discovery.txt`

---

## Lab 2 – TCP Connect Scan

### Objective

Identify open TCP ports using a complete TCP three-way handshake.

### Command

```bash
nmap -sT 192.168.56.10
```

### Description

Performed a TCP Connect Scan against the target to enumerate open ports.

### Evidence

- Screenshot:
  - `nmap-screenshots/02-tcp-connect-scan.png`

- Raw Output:
  - `evidence/tcp-connect.txt`

---

## Lab 3 – SYN Scan

### Objective

Perform a stealthier half-open TCP scan.

### Command

```bash
sudo nmap -sS 192.168.56.10
```

### Description

Performed a SYN Scan to enumerate ports without completing the TCP handshake.

### Evidence

- Screenshot:
  - `nmap-screenshots/03-syn-scan.png`

- Raw Output:
  - `evidence/syn-scan.txt`

---

## Lab 4 – Service Version Detection

### Objective

Identify services and application versions running on open ports.

### Command

```bash
nmap -sV 192.168.56.10
```

### Description

Enumerated running services and software versions.

### Evidence

- Screenshot:
  - `nmap-screenshots/04-service-version.png`

- Raw Output:
  - `evidence/service-version.txt`

---

## Lab 5 – Operating System Detection

### Objective

Identify operating systems using TCP/IP fingerprinting.

### Commands

```bash
sudo nmap -O 192.168.56.10
```

```bash
sudo nmap -O 192.168.56.30
```

```bash
sudo nmap -O 192.168.56.40
```

### Results

| Target | Detection |
|---------|-----------|
| Metasploitable 2 | Linux Kernel 2.6.x |
| Ubuntu Desktop | Linux detected |
| Windows 11 | OS fingerprint inconclusive due to filtered ports |

### Evidence

- Screenshot:
  - `nmap-screenshots/05-os-detection.png`

- Raw Outputs:
  - `evidence/os-metasploitable.txt`
  - `evidence/os-ubuntu.txt`
  - `evidence/os-windows.txt`

---

## Lab 6 – NSE Vulnerability Scanning

### Objective

Identify known vulnerabilities using the Nmap Scripting Engine.

### Command

```bash
sudo nmap --script vuln 192.168.56.10
```

### Key Findings

- vsFTPd 2.3.4 Backdoor (CVE-2011-2523)
- Logjam (CVE-2015-4000)
- POODLE (CVE-2014-3566)
- Slowloris Denial of Service
- Java RMI Remote Code Execution
- UnrealIRCd Backdoor

### Evidence

- Screenshot:
  - `nmap-screenshots/06-nse-vulnerability-scan.png`

- Raw Output:
  - `evidence/nse-vuln.txt`

---

# Evidence Files

The repository includes the original Nmap output generated during each lab. These files serve as supporting evidence for the documented findings.

| Evidence File | Description |
|--------------|-------------|
| host-discovery.txt | Host Discovery Scan |
| tcp-connect.txt | TCP Connect Scan |
| syn-scan.txt | SYN Scan |
| service-version.txt | Service Version Detection |
| os-metasploitable.txt | OS Detection (Metasploitable 2) |
| os-ubuntu.txt | OS Detection (Ubuntu Desktop) |
| os-windows.txt | OS Detection (Windows 11) |
| nse-vuln.txt | NSE Vulnerability Scan |

---

# Skills Demonstrated

- Host Discovery
- TCP Connect Scanning
- SYN Scanning
- Port Enumeration
- Service Enumeration
- Version Detection
- Operating System Fingerprinting
- Vulnerability Assessment
- Nmap Scripting Engine (NSE)
- Linux Command Line
- Technical Documentation

---

# MITRE ATT&CK Mapping

| Technique | Description |
|-----------|-------------|
| T1595 | Active Scanning |
| T1046 | Network Service Discovery |

---

# Repository Structure

```text
Network-Scanning/
│
├── README.md
│
├── evidence/
│   ├── host-discovery.txt
│   ├── tcp-connect.txt
│   ├── syn-scan.txt
│   ├── service-version.txt
│   ├── os-metasploitable.txt
│   ├── os-ubuntu.txt
│   ├── os-windows.txt
│   └── nse-vuln.txt
│
└── nmap-screenshots/
    ├── 01-host-discovery.png
    ├── 02-tcp-connect-scan.png
    ├── 03-syn-scan.png
    ├── 04-service-version.png
    ├── 05-os-detection.png
    └── 06-nse-vulnerability-scan.png
```

---

# Key Learnings

- Discovered live hosts using ICMP and ARP-based discovery.
- Compared TCP Connect and SYN scan techniques.
- Enumerated services and software versions running on target systems.
- Performed operating system fingerprinting using TCP/IP stack analysis.
- Identified vulnerable services using the Nmap Scripting Engine.
- Improved practical understanding of the reconnaissance phase of cybersecurity assessments.
- Strengthened technical documentation skills by recording evidence and screenshots for each lab.

---

# Future Improvements

- Perform UDP Scanning (`-sU`)
- Explore Firewall Evasion techniques
- Automate scans using Bash scripts
- Perform IPv6 Network Reconnaissance
- Compare Nmap with Masscan
- Integrate scan results into Wazuh SIEM for alert correlation

---

# Disclaimer

This project was conducted in a controlled home lab environment for educational and defensive cybersecurity purposes only. All scans were performed against systems owned by or explicitly authorized for testing. Unauthorized scanning of networks or systems without permission is illegal and unethical.