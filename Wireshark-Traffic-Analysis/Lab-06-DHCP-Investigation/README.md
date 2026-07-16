# DHCP Traffic Analysis Using Wireshark

## Objective

Capture and analyze the Dynamic Host Configuration Protocol (DHCP) communication between a client and a DHCP server. This investigation focuses on understanding the complete DORA (Discover, Offer, Request, Acknowledge) process used to automatically assign network configuration to a client.

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Kali Linux | DHCP Client / Analyst | 10.0.2.15 |
| VirtualBox NAT DHCP Server | DHCP Server | 10.0.2.2 |

---

# Tools Used

- Wireshark
- Kali Linux
- dhclient
- VirtualBox

---

# Protocols Analyzed

- DHCP
- UDP
- IPv4
- Ethernet II

---

# Investigation Scenario

A DHCP client requested network configuration from a DHCP server after releasing its existing IP lease. The communication was captured in Wireshark to analyze each stage of the DHCP DORA process.

---

# Investigation Process

## Step 1 – Release Existing DHCP Lease

The current DHCP lease was released using:

```bash
sudo dhclient -r eth0
```

A new DHCP request was generated using:

```bash
sudo dhclient -v eth0
```

---

## Step 2 – Capture DHCP Traffic

Started packet capture on the **eth0** interface and applied the following display filter:

```text
bootp
```

This filter displays DHCP packets in Wireshark.

---

## Step 3 – DHCP Discover

The client initiated communication by broadcasting a DHCP Discover message.

### Key Observations

- Source IP: **0.0.0.0**
- Destination IP: **255.255.255.255**
- Source Port: **68**
- Destination Port: **67**
- Transaction ID: **0xd3db3231**
- Message Type: **Discover**

The client broadcasts this request because it has not yet been assigned an IP address.

---

## Step 4 – DHCP Offer

The DHCP server responded with an available IP address.

### Key Observations

- DHCP Server: **10.0.2.2**
- Offered IP Address: **10.0.2.15**
- Lease Time: **1 Day**
- Subnet Mask: **255.255.255.0**
- Default Gateway: **10.0.2.2**
- DNS Server: **192.168.149.253**

---

## Step 5 – DHCP Request

The client requested the offered IP address from the DHCP server.

### Key Observations

- Requested IP Address: **10.0.2.15**
- DHCP Server Identifier: **10.0.2.2**
- Message Type: **Request**

This message informs the DHCP server that the client accepts the offered IP address.

---

## Step 6 – DHCP ACK

The DHCP server confirmed the lease and assigned the IP address.

### Key Observations

- Assigned IP Address: **10.0.2.15**
- Lease Time: **1 Day**
- Default Gateway: **10.0.2.2**
- DNS Server: **192.168.149.253**
- Message Type: **ACK**

After receiving the DHCP ACK, the client configures its network settings and begins normal communication.

---

# Investigation Findings

- Successfully captured the complete DHCP DORA process.
- Observed communication over UDP ports **67** and **68**.
- Verified that the Transaction ID remained consistent throughout the exchange.
- Identified the assigned IP address, subnet mask, gateway, DNS server, and lease time.
- Confirmed successful IP address assignment by the DHCP server.

---

# SOC Investigation Notes

Monitoring DHCP traffic helps identify network anomalies and potential attacks.

Examples include:

- Rogue DHCP Servers
- DHCP Starvation Attacks
- Unauthorized devices requesting IP addresses
- Incorrect gateway or DNS server assignments
- DHCP lease abuse

Analyzing DHCP traffic enables SOC analysts to detect malicious network configuration attempts before they impact users.

---

# Evidence

The original packet capture used during this investigation is available in the **Evidence** folder.

```text
Evidence/
└── DHCP.pcapng
```

---

# Screenshots

## DHCP Discover

![DHCP Discover](Screenshots/01-dhcp-discover.png)

---

## DHCP Offer

![DHCP Offer](Screenshots/02-dhcp-offer.png)

---

## DHCP Request

![DHCP Request](Screenshots/03-dhcp-request.png)

---

## DHCP ACK

![DHCP ACK](Screenshots/04-dhcp-ack.png)

---

## DHCP DORA Overview

![DORA Process](Screenshots/05-dora-overview.png)

---

# Skills Practiced

- DHCP Traffic Analysis
- Wireshark Packet Analysis
- DORA Process Investigation
- UDP Protocol Analysis
- Network Configuration Analysis
- Network Troubleshooting
- Packet Inspection
- SOC Investigation Methodology

---

# Key Learnings

- Understood the complete DHCP DORA process.
- Learned how clients obtain IP addresses dynamically.
- Identified DHCP communication over UDP ports 67 and 68.
- Analyzed DHCP options including gateway, DNS server, subnet mask, and lease time.
- Learned how SOC analysts investigate rogue DHCP servers and DHCP starvation attacks.
- Improved practical packet analysis skills using Wireshark.

---

# Conclusion

This investigation provided hands-on experience analyzing DHCP traffic using Wireshark. By examining each stage of the DORA process, I gained a deeper understanding of dynamic IP address assignment and the security considerations associated with DHCP. Understanding DHCP behavior is essential for SOC analysts when investigating network configuration issues, rogue DHCP servers, and DHCP-based attacks.