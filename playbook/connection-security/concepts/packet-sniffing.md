# Packet Sniffing

## Overview

Packet sniffing is the process of capturing and analyzing network traffic as it travels across a network. Security professionals use packet sniffing to troubleshoot network issues, analyze protocols, investigate security incidents, and identify suspicious or malicious activity.

Packet sniffing is commonly performed using packet analyzers such as Wireshark, which can capture live traffic or analyze previously saved packet capture (PCAP) files.

## Key Concepts

### Packets

Network communication is broken into small units called packets.

Each packet typically contains:

- Header information
- Payload (the transmitted data)

By examining packets, analysts can understand how devices communicate across a network.

### Passive Sniffing

Passive sniffing captures network traffic without modifying or interfering with communications.

It is commonly used for:

- Network monitoring
- Troubleshooting
- Protocol analysis
- Incident response
- Malware analysis

### Promiscuous Mode

Normally, a network interface processes only traffic addressed to it.

In promiscuous mode, the interface accepts all packets it can observe, allowing packet capture software to inspect more network traffic.

### Packet Capture Files (PCAP)

Captured traffic can be saved as a Packet Capture (PCAP) file for later analysis, sharing, or forensic investigation.

### Encrypted Traffic

Packet sniffers can capture encrypted traffic, but they generally cannot read the encrypted payload without the appropriate decryption keys.

However, metadata such as:

- Source and destination IP addresses
- Port numbers
- Protocols
- Packet sizes
- Timing information

typically remains visible.

## Why It Matters

Packet sniffing provides visibility into network communications and is one of the most important techniques used for troubleshooting, incident response, digital forensics, malware analysis, and protocol analysis.

Attackers may also use packet sniffing to intercept unencrypted credentials and sensitive information, making encryption an essential security control.

## Common Uses

- Troubleshoot network connectivity
- Analyze network protocols
- Investigate suspicious traffic
- Verify application communications
- Capture evidence during incident response
- Analyze malware communications
- Review PCAP files

## Best Practices

- Capture only traffic you are authorized to monitor.
- Use encrypted protocols to protect sensitive communications.
- Capture only the traffic needed for analysis.
- Use display filters to reduce unnecessary packets.
- Secure PCAP files because they may contain sensitive information.
