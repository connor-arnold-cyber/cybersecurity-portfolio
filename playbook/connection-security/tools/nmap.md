# Nmap

## Overview

Nmap (Network Mapper) is an open-source network discovery and security auditing tool used to identify hosts, open ports, running services, operating systems, and network configurations.

It is one of the most commonly used tools during reconnaissance and vulnerability assessments.

## Key Concepts

### Host Discovery

Nmap can determine whether a host is online before performing a port scan.

### Port Scanning

Nmap identifies open, closed, and filtered ports to determine which network services are accessible.

Common scan types include:

- TCP Connect (`-sT`)
- SYN Scan (`-sS`)
- UDP Scan (`-sU`)
- FIN Scan (`-sF`)
- NULL Scan (`-sN`)
- Xmas Scan (`-sX`)
- ACK Scan (`-sA`)

### Service Detection

Using service detection (`-sV`), Nmap attempts to identify the application and version running on an open port.

### Operating System Detection

Operating system detection (`-O`) analyzes network responses to estimate the target's operating system.

### Nmap Scripting Engine (NSE)

The Nmap Scripting Engine allows scripts to automate tasks such as:

- Service enumeration
- Vulnerability detection
- Configuration auditing
- Information gathering

## Why It Matters

Nmap provides visibility into a network by identifying active hosts and exposed services. It is often the first tool used during network reconnaissance and serves as the foundation for many security assessments.

## Common Uses

- Host discovery
- Port scanning
- Service enumeration
- Operating system detection
- Network inventory
- Security auditing
- Vulnerability assessment preparation

## Best Practices

- Scan only systems you are authorized to assess.
- Start with host discovery before large scans.
- Use the least intrusive scan that meets your objective.
- Verify important findings manually.
- Document scan results for future comparison.
