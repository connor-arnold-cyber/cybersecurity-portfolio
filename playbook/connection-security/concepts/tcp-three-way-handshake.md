# TCP Three-Way Handshake

## Overview

The TCP Three-Way Handshake establishes a reliable connection between two devices before data is transmitted. It synchronizes both systems and confirms they are ready to communicate.

## Key Concepts

- SYN
- SYN-ACK
- ACK
- Initial Sequence Number (ISN)
- Connection establishment

## Why It Matters

Many attacks and defensive technologies involve the TCP handshake. Understanding how connections are established helps with packet analysis, intrusion detection, firewall configuration, and identifying attacks such as SYN floods.

## Common Uses

- HTTPS connections
- SSH sessions
- FTP connections
- Email communication
- Any TCP-based service

## Best Practices

- Recognize the SYN → SYN-ACK → ACK sequence.
- Understand how incomplete handshakes appear in packet captures.
- Know that TCP sessions always begin with this process.

## Related Labs & Projects

- Wireshark Three-Way Handshake Analysis
- TCP Packet Capture Lab
