# Firewalls

## Overview

A firewall is a security device or software application that monitors and controls network traffic based on predefined security rules. It acts as a barrier between trusted and untrusted networks, allowing authorized traffic while blocking unauthorized or potentially malicious connections.

Firewalls are one of the first lines of defense in network security.

## Key Concepts

### Traffic Filtering

A firewall examines network traffic and determines whether it should be allowed or blocked according to its configured rules.

Filtering decisions are commonly based on:

- Source IP address
- Destination IP address
- Source port
- Destination port
- Protocol (TCP, UDP, ICMP)
- Connection state

### Inbound and Outbound Traffic

Firewalls can control both:

- **Inbound traffic** entering a network
- **Outbound traffic** leaving a network

Monitoring outbound traffic helps prevent compromised systems from communicating with attackers.

### Rule Sets

Firewalls use ordered rule sets to determine how traffic should be handled.

Rules typically specify:

- What traffic is allowed
- What traffic is denied
- The order in which rules are evaluated

Most firewalls stop processing rules once a matching rule is found.

### Stateful Inspection

Stateful firewalls keep track of active network connections.

Instead of evaluating every packet independently, they determine whether a packet belongs to an existing, legitimate connection before allowing it to pass.

### Host-Based vs. Network Firewalls

**Host-based firewalls** run on individual computers and protect a single device.

Examples include:

- Windows Defender Firewall
- Linux firewalld
- pf (macOS)

**Network firewalls** protect multiple devices by filtering traffic as it passes between networks.

## Why It Matters

Firewalls reduce an organization's attack surface by limiting which network services can be reached. They help prevent unauthorized access, enforce security policies, and protect systems from many common network attacks.

While a firewall cannot stop every attack, it is a fundamental layer in a defense-in-depth security strategy.

## Common Uses

- Restrict network access
- Block unauthorized connections
- Allow only approved services
- Segment networks
- Protect internal systems
- Enforce organizational security policies
- Monitor network traffic

## Best Practices

- Follow the principle of least privilege when creating firewall rules.
- Deny unnecessary ports and services by default.
- Review firewall rules regularly and remove obsolete entries.
- Log firewall activity to assist with troubleshooting and incident response.
- Keep firewall software and firmware up to date.
