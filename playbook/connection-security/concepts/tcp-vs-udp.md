# TCP vs UDP

## Overview

TCP and UDP are the two primary transport-layer protocols used by TCP/IP. TCP focuses on reliable communication, while UDP prioritizes speed and low overhead.

## Key Concepts

- TCP is connection-oriented.
- UDP is connectionless.
- TCP guarantees delivery.
- UDP does not guarantee delivery.
- TCP uses acknowledgments and retransmissions.
- UDP has lower overhead and latency.

## Why It Matters

Many network services, attacks, and security tools behave differently depending on whether they use TCP or UDP. Understanding both protocols is essential for troubleshooting, packet analysis, firewall configuration, and penetration testing.

## Common Uses

TCP:
- HTTPS
- SSH
- FTP
- SMTP

UDP:
- DNS
- VoIP
- Video streaming
- Online gaming

## Best Practices

- Use TCP when reliability is required.
- Use UDP when speed is more important than guaranteed delivery.
- Know which common services use each protocol.

## Related Labs & Projects

- Wireshark TCP Analysis
- UDP Traffic Analysis
- Port Scanning Lab
