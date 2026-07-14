# Wireshark Traffic Analysis

## Overview

This section documents my hands-on Wireshark investigations performed in an isolated cybersecurity home lab.

The purpose of these labs is to develop practical packet analysis skills by observing normal network communication, investigating malicious traffic, and documenting findings using a structured SOC analyst workflow.

---

# Table of Contents

- Overview
- Lab Environment
- Tools Used
- Protocol Summary
- Traffic Analysis Highlights
- Completed Labs
- Skills Matrix
- Why These Labs Matter
- Investigation Workflow
- Upcoming Labs

---

# Lab Environment

| Machine | Role |
|----------|------|
| Kali Linux | Security Analyst / Attacker |
| Windows 11 | Endpoint |
| Metasploitable 2 | Vulnerable Server |
| VirtualBox Internal Network | Isolated Lab Network |

---

# Tools Used

- Wireshark
- Kali Linux
- Windows 11
- Metasploitable 2
- VirtualBox
- Mozilla Firefox

---

# Protocol Summary

| Protocol | Purpose | Status |
|----------|---------|:------:|
| ICMP | Network connectivity testing | ✅ |
| ARP | IP to MAC address resolution | ✅ |
| TCP | Reliable communication | ✅ |
| DNS | Domain name resolution | ✅ |
| HTTP | Web traffic analysis | ✅ |
| HTTPS/TLS | Secure web traffic analysis | ✅ |
| DHCP | Automatic IP configuration | 🚧 |

---

# Traffic Analysis Highlights

## ICMP Analysis

Generated ICMP traffic using the `ping` command and analyzed Echo Request and Echo Reply packets.

```bash
ping 192.168.56.10
```

![ICMP Packet Analysis](wireshark-screenshots/icmp-packet-analysis.png)

---

## ARP Analysis

Observed ARP Request and ARP Reply packets used for IP-to-MAC address resolution inside the local network.

![ARP Traffic Analysis](wireshark-screenshots/arp-traffic-analysis.png)

---

## TCP Three-Way Handshake

Captured and analyzed the TCP connection establishment process.

Observed:

- SYN
- SYN-ACK
- ACK

![TCP Handshake Analysis](wireshark-screenshots/tcp-handshake-analysis.png)

---

# Completed Labs

## ✅ Lab 01 – Network Troubleshooting

### Objective

Investigated basic network connectivity by analyzing ICMP, ARP, and TCP traffic inside the home lab.

### Topics Covered

- Network Connectivity
- ICMP Analysis
- ARP Analysis
- TCP Three-Way Handshake
- Packet Capture
- Network Troubleshooting

📂 **Lab Folder**

[Lab-01-Network-Troubleshooting](Lab-01-Network-Troubleshooting)

---

## ✅ Lab 02 – ARP Spoofing Investigation

### Objective

Performed a controlled ARP Spoofing attack, analyzed forged ARP packets, investigated ARP cache poisoning, and verified successful recovery.

### Topics Covered

- ARP Protocol
- ARP Cache
- ARP Spoofing
- Man-in-the-Middle (MITM)
- Wireshark Packet Analysis
- Root Cause Analysis
- Evidence Collection
- Recovery Validation

📂 **Lab Folder**

[Lab-02-ARP-Spoofing-Investigation](Lab-02-ARP-Spoofing-Investigation)

---

## ✅ Lab 03 – DNS Investigation

### Objective

Captured and analyzed DNS traffic to understand how domain names are resolved into IP addresses, examining DNS query and response packets in detail.

### Topics Covered

- DNS Query/Response Analysis
- UDP Protocol Analysis
- Transaction ID Correlation
- DNS Resource Records (A Records)
- DNS TTL and Caching
- Packet Inspection

📂 **Lab Folder**

[Lab-03-DNS-Investigation](Lab-03-DNS-Investigation)

---

## ✅ Lab 04 – HTTP Investigation

### Objective

Captured and analyzed HTTP traffic to understand how browsers communicate with web servers, investigating requests, responses, headers, and full TCP stream reconstruction.

### Topics Covered

- HTTP Request/Response Analysis
- HTTP Header Inspection
- TCP Stream Reconstruction
- Plaintext Traffic Risk (SOC Perspective)
- Web Traffic Investigation

📂 **Lab Folder**

[Lab-04-HTTP-Investigation](Lab-04-HTTP-Investigation)

---

## ✅ Lab 05 – HTTPS/TLS Investigation

### Objective

Analyzed HTTPS traffic and the TLS handshake process to understand what metadata remains visible even when application data is encrypted.

### Topics Covered

- TLS Handshake Analysis (Client Hello / Server Hello)
- Server Name Indication (SNI)
- Certificate Inspection and Validation
- Cipher Suite Identification
- TLS Version Analysis
- Encrypted Traffic Investigation (SOC Perspective)

📂 **Lab Folder**

[Lab-05-HTTPS-TLS-Investigation](Lab-05-HTTPS-TLS-Investigation)

---

# Skills Matrix

| Skill | Lab 01 | Lab 02 | Lab 03 | Lab 04 | Lab 05 |
|--------|:------:|:------:|:------:|:------:|:------:|
| Wireshark | ✅ | ✅ | ✅ | ✅ | ✅ |
| ICMP Analysis | ✅ | | | | |
| ARP Analysis | ✅ | ✅ | | | |
| TCP Analysis | ✅ | | | ✅ | |
| DNS Analysis | | | ✅ | | |
| HTTP Analysis | | | | ✅ | |
| TLS/HTTPS Analysis | | | | | ✅ |
| Packet Filtering | ✅ | ✅ | ✅ | ✅ | ✅ |
| Packet Capture | ✅ | ✅ | ✅ | ✅ | ✅ |
| Incident Investigation | | ✅ | | | |
| Root Cause Analysis | | ✅ | | | |
| MITM Concepts | | ✅ | | | |
| Certificate Validation | | | | | ✅ |

---

# Skills Developed

## Networking

- TCP/IP
- ICMP
- ARP
- TCP
- DNS
- HTTP
- TLS/HTTPS

## Packet Analysis

- Packet Capture
- Packet Filtering
- Protocol Analysis
- Traffic Investigation
- TCP Stream Reconstruction

## Cybersecurity

- ARP Spoofing
- Man-in-the-Middle (MITM)
- Network Investigation
- Incident Analysis
- Root Cause Analysis
- Evidence Collection
- Certificate Validation
- Encrypted Traffic Analysis

---

# Why These Labs Matter

These investigations simulate tasks commonly performed by SOC Analysts and Blue Team professionals.

The labs focus on:

- Investigating network connectivity issues
- Analyzing packet captures
- Understanding network protocols
- Detecting suspicious network behavior
- Collecting forensic evidence
- Investigating attack techniques
- Validating recovery after security incidents
- Analyzing encrypted traffic metadata

---

# Investigation Workflow

Every lab follows the same investigation methodology.

```text
Scenario
      │
      ▼
Understand the Protocol
      │
      ▼
Build the Lab
      │
      ▼
Observe Normal Behaviour
      │
      ▼
Perform Hands-on Activity
      │
      ▼
Capture Network Traffic
      │
      ▼
Analyze Evidence
      │
      ▼
Investigate Findings
      │
      ▼
Recover
      │
      ▼
Document Results
```

---

# Upcoming Labs

- DHCP Analysis
- FTP Traffic Analysis
- SSH Packet Analysis
- SMB Analysis
- NAT Investigation
- VLAN Traffic Analysis

---

# Goal

The objective of this repository is to build practical packet analysis and network investigation skills through hands-on cybersecurity labs rather than theory alone.

Each lab is documented with:

- Objectives
- Lab Setup
- Commands Used
- Screenshots
- Packet Captures
- Evidence
- Analysis
- Recovery Steps
- Lessons Learned

This approach helps strengthen both networking fundamentals and SOC investigation skills.
