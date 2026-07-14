# DNS Investigation Using Wireshark

## Objective

Capture and analyze DNS traffic using Wireshark to understand how domain names are resolved into IP addresses. This investigation focuses on examining DNS queries and responses, identifying key protocol fields, and understanding the role of DNS in network communication.

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Kali Linux | Analyst Machine | 10.0.2.15 |
| DNS Server | Resolver | 192.168.149.253 |

---

# Tools Used

- Wireshark
- Kali Linux
- Firefox Web Browser

---

# Protocol Analyzed

- DNS (Domain Name System)
- UDP
- IPv4
- Ethernet II

---

# Investigation Steps

### Step 1: Generate DNS Traffic

Opened a web browser and visited **google.com** to generate DNS traffic.

---

### Step 2: Capture DNS Packets

Applied the following display filter:

```text
dns
```

Captured both DNS queries and responses.

---

### Step 3: Analyze DNS Query

Observed the client sending a DNS request to resolve the domain name.

Key observations:

- Source IP: 10.0.2.15
- Destination IP: 192.168.149.253
- Source Port: 47592
- Destination Port: 53
- Transaction ID: 0x707a
- Query Type: A
- Domain: google.com

---

### Step 4: Analyze DNS Response

Examined the DNS server's response.

Key observations:

- Transaction ID matched the query
- Flags: 0x8180 (Standard Query Response, No Error)
- Question Count: 1
- Answer Records: 6
- Multiple IPv4 addresses returned for google.com

---

# Investigation Findings

- DNS uses UDP port 53 for fast communication.
- The Transaction ID is used to match DNS responses with their corresponding queries.
- The response contained multiple A records for the requested domain.
- DNS successfully resolved the domain name into IPv4 addresses.
- The response indicated **No Error**, confirming successful name resolution.

---

# Evidence

The original packet capture used during this investigation is available in the **Evidence** folder.

```
Evidence/
└── DNS.pcapng
```

---

# Screenshots

## DNS Query

![DNS Query](Screenshots/01-dns-query.png)

---

## DNS Response

![DNS Response](Screenshots/02-dns-response.png)

---

## DNS Packet Details

![DNS Packet Details](Screenshots/03-dns-packet-details.png)

---

# Skills Practiced

- DNS packet analysis
- Wireshark filtering
- Protocol analysis
- Network troubleshooting
- Traffic investigation
- Packet inspection
- Understanding DNS resolution

---

# Key Learnings

- Learned how DNS translates domain names into IP addresses.
- Understood the difference between DNS queries and responses.
- Identified important DNS fields such as Transaction ID, Flags, Questions, and Answers.
- Observed how UDP enables fast DNS communication.
- Practiced analyzing DNS traffic using Wireshark.

---

# Conclusion

This investigation provided hands-on experience with DNS traffic analysis using Wireshark. By examining both DNS queries and responses, I gained a deeper understanding of the DNS resolution process and strengthened my network traffic analysis skills, which are essential for SOC analysts and cybersecurity professionals.
