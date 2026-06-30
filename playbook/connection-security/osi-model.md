# OSI Model

## Overview

The Open Systems Interconnection (OSI) Model is a seven-layer framework used to describe how data travels between devices on a network. Each layer has a specific responsibility and works with the layers above and below it to enable communication.

Although modern networks use the TCP/IP model, the OSI Model remains the industry standard for learning networking and troubleshooting.

---

## Layers

| Layer | Name | Primary Function | Common Examples |
|--------|------|------------------|-----------------|
| 7 | Application | Provides network services to user applications. | HTTP, HTTPS, DNS, SMTP, FTP |
| 6 | Presentation | Formats, encrypts, and compresses data. | TLS/SSL, JPEG, ASCII |
| 5 | Session | Establishes, manages, and terminates communication sessions. | NetBIOS, RPC |
| 4 | Transport | Provides reliable end-to-end communication. | TCP, UDP |
| 3 | Network | Routes packets between networks. | IP, ICMP, Routers |
| 2 | Data Link | Transfers frames between devices on the same network. | Ethernet, MAC Addresses, Switches |
| 1 | Physical | Transmits raw bits over physical media. | Cables, Fiber, Wireless Signals |

---

## How Data Moves Through the OSI Model

When sending data:

Application → Presentation → Session → Transport → Network → Data Link → Physical

When receiving data:

Physical → Data Link → Network → Transport → Session → Presentation → Application

This process is known as **encapsulation** and **decapsulation**.

---

## Common Devices

| Device | OSI Layer |
|----------|-----------|
| Hub | Layer 1 |
| Switch | Layer 2 |
| Router | Layer 3 |
| Firewall | Layers 3–7 (depending on type) |

---

## Why It Matters

Understanding the OSI Model helps you:

- Troubleshoot network problems
- Understand where protocols operate
- Identify where attacks occur
- Understand how data moves through a network

Nearly every networking certification, including Network+, Security+, and CCNA, expects a solid understanding of the OSI Model.

---

## Related Concepts

- TCP/IP Model
- Encapsulation
- Packets
- Frames
- IP Addressing
- Ports and Protocols

---

## Related Labs & Projects

- Cisco Packet Tracer
- Wireshark Packet Analysis
- Network Troubleshooting Labs
- TryHackMe: Network Fundamentals
