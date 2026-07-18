# Evidence - Lab 01 Network Connectivity Troubleshooting

## Overview

This directory contains the evidence collected during the **Lab 01 - Network Connectivity Troubleshooting Using ICMP, ARP, and Windows Firewall** investigation.

The collected artifacts support the troubleshooting process, validate the identified root cause, and confirm successful remediation through packet analysis and network testing.

---

# Evidence Inventory

| Evidence ID | File | Description |
|------------|------|-------------|
| E-01 | network-troubleshooting.pcapng | Complete Wireshark packet capture containing ARP and ICMP traffic generated during the investigation. |

---

# Evidence Description

## E-01 - Network Packet Capture

**File:** `network-troubleshooting.pcapng`

### Purpose

This packet capture was collected using Wireshark to analyze network communication between the Kali Linux analyst workstation and the Windows 11 endpoint.

### Observed Traffic

- ARP Request
- ARP Reply
- ICMP Echo Request
- ICMP Echo Reply

### Key Findings

- ARP resolution occurred before ICMP communication.
- The destination MAC address was successfully resolved.
- ICMP Echo Requests were transmitted after ARP resolution.
- Windows responded with ICMP Echo Replies after the Windows Defender Firewall rule was enabled.
- Packet capture confirmed successful Layer 2 and Layer 3 communication.

---

# Chain of Evidence

The investigation followed the sequence below:

1. Verified IP configuration.
2. Performed initial ICMP connectivity test.
3. Observed failed communication.
4. Investigated Windows Defender Firewall configuration.
5. Enabled the ICMP Echo Request inbound rule.
6. Repeated the connectivity test.
7. Captured network traffic using Wireshark.
8. Verified successful ARP resolution and ICMP communication.

---

# Conclusion

The packet capture serves as supporting evidence that the connectivity issue was caused by a host-based firewall configuration rather than a network connectivity problem. The captured traffic validates both the troubleshooting process and the successful resolution of the issue.
