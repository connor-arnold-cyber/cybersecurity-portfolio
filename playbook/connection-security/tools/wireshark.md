# Wireshark

## Overview

Wireshark is an open-source packet analyzer used to capture and inspect network traffic in real time or from previously captured packet capture (PCAP) files.

It allows analysts to examine individual packets, troubleshoot network issues, and investigate security events.

## Key Concepts

### Packet Capture

Wireshark captures packets transmitted across a network interface and displays them for analysis.

Each captured packet contains information such as:

- Source and destination IP addresses
- Source and destination ports
- Protocol
- Packet length
- Timestamp

### Packet Details

Selecting a packet reveals its contents organized by protocol layers.

Depending on the protocol, information may include:

- Ethernet
- IP
- TCP or UDP
- HTTP
- DNS
- TLS

### Display Filters

Display filters allow you to view only packets matching specific criteria without modifying the capture.

Examples:

- `http`
- `dns`
- `tcp.port == 80`
- `ip.addr == 192.168.1.10`

### PCAP Files

Wireshark can save captured traffic as a PCAP file for later analysis or sharing with other analysts.

## Why It Matters

Wireshark provides visibility into network communications, making it one of the most valuable tools for troubleshooting, incident response, malware analysis, and protocol analysis.

## Common Uses

- Analyze network traffic
- Troubleshoot connectivity issues
- Investigate security incidents
- Examine network protocols
- Verify application communications
- Analyze PCAP files

## Best Practices

- Capture only traffic you are authorized to monitor.
- Apply display filters to reduce unnecessary traffic.
- Save important captures for future analysis.
- Protect PCAP files, as they may contain sensitive information.
- Use encrypted protocols whenever possible to protect sensitive data in transit.
