# Lab: DoS Traffic Capture with LOIC and tcpdump

## Overview

This lab demonstrated how different denial-of-service (DoS) attacks generate network traffic and how packet capture tools can be used to observe and analyze that traffic. Multiple protocol-specific floods were generated using LOIC while tcpdump captured the traffic for later inspection with capinfos, illustrating how analysts can verify and examine attack activity.

## Lab Summary

This lab follows the lifecycle of denial-of-service traffic analysis:

1. Prepared a Linux packet capture system and verified the network configuration.
2. Captured network traffic while TCP, UDP, HTTP, and HTTP floods were generated using LOIC.
3. Analyzed each packet capture using capinfos to verify the captured traffic.
4. Examined web server logs to observe the effects of the HTTP flood.

## Key Takeaways

- Packet captures provide evidence of network attacks for later analysis.
- Different DoS methods generate different network traffic patterns.
- tcpdump can capture raw network traffic directly from an interface.
- capinfos provides useful statistics about packet capture files.
- HTTP floods generate activity that can be verified through web server logs.
- Multiple protocols can be targeted during denial-of-service attacks.
- Packet captures help validate that attacks occurred as expected.

## Workflow

### Prepare the Packet Capture System

The Linux Sniffer was configured and prepared to capture traffic throughout the lab.

**Purpose**

- Verify the network interface configuration.
- Remove the IPv4 address from the capture interface.
- Prepare tcpdump to capture traffic.

**Result**

- The Linux Sniffer successfully captured traffic on the eth0 interface.

### Generate TCP Flood Traffic

LOIC was configured to perform a TCP flood against the target while tcpdump recorded the traffic.

**Purpose**

- Generate TCP flood traffic.
- Capture the resulting packets for analysis.

**Result**

- TCP traffic was successfully captured and saved to `TCPcapture.cap`.

### Generate UDP Flood Traffic

LOIC was reconfigured to perform a UDP flood while tcpdump recorded the traffic.

**Purpose**

- Compare UDP flood traffic with TCP flood traffic.
- Produce a separate capture file for analysis.

**Result**

- UDP traffic was successfully captured and saved to `UDPcapture.cap`.

### Generate HTTP Flood Traffic

LOIC was configured to generate HTTP requests while packet captures were collected.

**Purpose**

- Observe how HTTP-based floods appear in captured traffic.
- Compare application-layer traffic with transport-layer floods.

**Result**

- HTTP traffic was captured and saved to `HTTPcapture.cap`.

### Generate HTTP Flood Without Waiting for Replies

The HTTP flood was repeated with the "Wait for reply" option disabled.

**Purpose**

- Increase request generation speed.
- Observe differences in captured traffic volume.

**Result**

- Traffic was captured and saved to `HTTP2capture.cap`.

### Analyze Packet Capture Files

Each packet capture file was examined using capinfos.

**Purpose**

- Verify that packets were successfully captured.
- Review packet counts and capture statistics.

**Result**

- Packet counts and capture statistics were successfully displayed for each capture file.

### Examine Web Server Logs

The Apache access log on the Windows Server was reviewed.

**Purpose**

- Verify that the HTTP flood reached the web server.
- Observe the server's recorded requests.

**Result**

- HTTP requests generated during the flood were visible within the Apache access log.

## Notes

### DoS Traffic Capture Process

```text
LOIC
   │
   ▼
Target Network
   │
   ▼
tcpdump Capture
   │
   ▼
PCAP File
   │
   ▼
capinfos Statistics
```

### tcpdump vs capinfos

tcpdump captures live network traffic directly from an interface and stores it as a packet capture file. capinfos does not inspect packet contents but instead summarizes information about an existing capture, including packet counts, capture duration, file size, and data rates.

### Protocol Comparison

The lab demonstrated denial-of-service traffic using multiple protocols. TCP and UDP floods target transport-layer protocols, while HTTP floods target the application layer by overwhelming web services with HTTP requests.

## Commands Used

### Network Configuration

```bash
ifconfig
ifconfig > ip1.txt
cat ip1.txt
cat ip2.txt
ifconfig eth0 0.0.0.0 up
```

### Packet Capture

```bash
tcpdump --help

tcpdump -i eth0 -nntttt -s 0 -w TCPcapture.cap

tcpdump -i eth0 -nntttt -s 0 -w UDPcapture.cap

tcpdump -i eth0 -nntttt -s 0 -w HTTPcapture.cap

tcpdump -i eth0 -nntttt -s 0 -w HTTP2capture.cap
```

### Packet Analysis

```bash
capinfos TCPcapture.cap

capinfos UDPcapture.cap

capinfos HTTPcapture.cap

capinfos HTTP2capture.cap
```

## Quick Reference

| Item | Purpose |
|------|---------|
| LOIC | Generate denial-of-service traffic |
| tcpdump | Capture live network traffic |
| capinfos | Display packet capture statistics |
| TCPcapture.cap | TCP flood packet capture |
| UDPcapture.cap | UDP flood packet capture |
| HTTPcapture.cap | HTTP flood packet capture |
| HTTP2capture.cap | HTTP flood capture without waiting for replies |
| Apache access.log | Verify HTTP requests reached the server |

## Related Playbook Pages

- [Denial of Service (DoS)](../concepts/dos-denial-of-service.md)
- [Distributed Denial of Service (DDoS)](../concepts/ddos-distributed-denial-of-service.md)
- [Packet Sniffing](../concepts/packet-sniffing.md)
- [HTTP](../concepts/http-hypertext-transfer-protocol.md)
- [TCP vs UDP](../concepts/tcp-vs-udp.md)
- [Wireshark](../tools/wireshark.md)
- [Nmap](../tools/nmap.md)
- [tcpdump](../tools/tcpdump.md) (coming soon)
- [capinfos](../tools/capinfos.md) (coming soon)
- [Low Orbit Ion Cannon (LOIC)](../tools/loic.md) (coming soon)
