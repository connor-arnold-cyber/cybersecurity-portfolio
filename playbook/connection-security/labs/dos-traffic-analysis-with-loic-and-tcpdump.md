# Lab: DOS Traffic Analysis With LOIC And TCPdump

## Overview

This lab demonstrates how denial-of-service attacks generate large volumes of network traffic, how packet captures can be used to analyze those attacks, and how tools such as tcpdump, capinfos, and LOIC can be used in an authorized testing environment to evaluate network availability and security controls.

## Lab Summary

This lab follows the lifecycle of a denial-of-service test:

1. Capture baseline network traffic.
2. Generate TCP and HTTP flood attacks with LOIC.
3. Capture and analyze network traffic using tcpdump.
4. Review packet statistics to evaluate attack behavior.

## Key Takeaways

- Packet captures provide evidence of network activity during a DoS attack.
- LOIC can generate TCP and HTTP floods for authorized security testing.
- capinfos quickly summarizes packet capture statistics.
- Traffic analysis helps validate network monitoring and incident response capabilities.

## Workflow

### Capture Baseline Traffic

Network traffic was captured on the Linux Sniffer using tcpdump before launching attack traffic.

**Purpose**

- Capture attack traffic for later analysis.
- Record packets exactly as they traversed the interface.
- Create packet capture files for forensic review.

**Result**

- TCPcapture.cap, HTTPcapture.cap, and HTTP2capture.cap were generated.

### Launch TCP Flood

LOIC was configured to perform a TCP flood against the target host while tcpdump recorded the traffic.

**Purpose**

- Generate high volumes of TCP traffic.
- Observe network behavior under load.
- Validate packet capture collection.

**Result**

- Large numbers of TCP packets were successfully captured.

### Launch HTTP Flood

LOIC generated an HTTP flood while tcpdump recorded HTTP traffic.

**Purpose**

- Simulate an application-layer denial-of-service attack.
- Compare HTTP traffic against the TCP flood.

**Result**

- HTTP traffic was successfully recorded for analysis.

### Launch HTTP2 Flood

A second HTTP flood was executed with the **Wait for reply** option disabled.

**Purpose**

- Increase the rate of transmitted requests.
- Observe the effect on captured packet volume.
- Compare packet statistics against the previous HTTP capture.

**Result**

- HTTP2capture.cap contained a significantly larger packet capture that was summarized using capinfos.

### Analyze Packet Capture

capinfos was used to examine the completed packet captures.

**Purpose**

- View packet capture statistics.
- Verify successful traffic collection.
- Confirm packet totals and capture duration.

**Result**

- Packet counts, capture duration, average packet size, and other metadata were displayed.

## Notes

### tcpdump

tcpdump is a command-line packet capture utility that records raw network traffic directly from an interface into a PCAP file for later analysis.

### LOIC

```text
LOIC
   │
   ▼
Generates TCP/HTTP Requests
   │
   ▼
Target Host
   │
   ▼
tcpdump Records Traffic
   │
   ▼
PCAP File
   │
   ▼
capinfos Summarizes Capture
```

### capinfos

capinfos provides a quick statistical summary of packet capture files, including packet count, capture duration, file size, average packet size, and data rate without opening the capture in Wireshark.

## Commands Used

### Capture Network Traffic

```bash
ifconfig
ifconfig > ip1.txt
cat ip1.txt
ifconfig eth0 0.0.0.0 up
tcpdump --help
tcpdump -i eth0 -nntttt -s 0 -w TCPcapture.cap
tcpdump -i eth0 -nntttt -s 0 -w HTTPcapture.cap
tcpdump -i eth0 -nntttt -s 0 -w HTTP2capture.cap
```

### Analyze Packet Captures

```bash
capinfos HTTPcapture.cap
capinfos HTTP2capture.cap
```

## Quick Reference

| Item | Purpose |
|------|---------|
| LOIC | Generate TCP and HTTP flood traffic |
| tcpdump | Capture network packets |
| capinfos | Summarize PCAP statistics |
| TCPcapture.cap | TCP flood packet capture |
| HTTPcapture.cap | HTTP flood packet capture |
| HTTP2capture.cap | HTTP flood capture with Wait for reply disabled |

## Related Playbook Pages

- [Denial of Service (DoS)](../concepts/dos-denial-of-service.md)
- [Distributed Denial of Service (DDoS)](../concepts/ddos-distributed-denial-of-service.md)
- [tcpdump](../tools/tcpdump.md)
- [Wireshark](../tools/wireshark.md)
- [Ping](../tools/ping.md)
