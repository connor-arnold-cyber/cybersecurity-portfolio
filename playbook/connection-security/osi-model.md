# OSI Model

## Overview

The Open Systems Interconnection (OSI) Model is a seven-layer framework used to describe how data travels between devices on a network. Each layer has a specific responsibility and works with the layers above and below it to enable communication.

Although modern networks use the TCP/IP model, the OSI Model remains the industry standard for learning networking and troubleshooting.

## Key Concepts

- Seven-Layer Networking Model
- Encapsulation
- Decapsulation
- Protocols
- Network Devices
- Data Flow
- Troubleshooting

### Layers

| Layer | Name | Primary Function | Common Examples |
|--------|------|------------------|-----------------|
| 7 | Application | Provides network services to user applications. | HTTP, HTTPS, DNS, SMTP, FTP |
| 6 | Presentation | Formats, encrypts, and compresses data. | TLS/SSL, JPEG, ASCII |
| 5 | Session | Establishes, manages, and terminates communication sessions. | NetBIOS, RPC |
| 4 | Transport | Provides reliable end-to-end communication. | TCP, UDP |
| 3 | Network | Routes packets between networks. | IP, ICMP, Routers |
| 2 | Data Link | Transfers frames between devices on the same network. | Ethernet, MAC Addresses, Switches |
| 1 | Physical | Transmits raw bits over physical media. | Cables, Fiber, Wireless Signals |

## Why It Matters

The OSI Model provides a standardized way to understand how networks function and communicate. It is one of the most important troubleshooting frameworks in networking because it helps isolate where communication problems occur.

Even though real-world networks use the TCP/IP model, cybersecurity professionals, network engineers, and certification exams frequently reference the OSI Model.

## Common Uses

- Network Troubleshooting
- Learning Network Protocols
- Understanding Packet Flow
- Mapping Network Devices
- Cybersecurity Training
- CompTIA Network+
- CompTIA Security+
- Cisco CCNA

## Best Practices

- Understand the primary responsibility of each layer.
- Learn which common protocols and devices operate at each layer.
- Use the model to troubleshoot network issues logically, starting at the most likely layer.
- Focus on understanding how data moves through the layers rather than memorizing them in isolation.

## Related Concepts

- TCP/IP Model
- Encapsulation
- Decapsulation
- Packets
- Frames
- IP Addressing
- Ports and Protocols
- Switching
- Routing

## Related Labs & Projects

- Cisco Packet Tracer
- Wireshark Packet Analysis
- Network Troubleshooting Labs
- TryHackMe: Network Fundamentals
