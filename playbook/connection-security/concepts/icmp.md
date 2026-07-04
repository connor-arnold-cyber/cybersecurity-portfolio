# Internet Control Message Protocol (ICMP)

## Overview

ICMP is a network protocol used to send diagnostic and error messages between devices. Unlike TCP and UDP, ICMP is not used to transport application data but to report network status and connectivity information.

## Key Concepts

- Echo Request
- Echo Reply
- Destination Unreachable
- Time Exceeded
- Ping
- Traceroute

## Why It Matters

ICMP is essential for network troubleshooting and is frequently encountered during penetration testing and incident response. Many reconnaissance techniques rely on ICMP, and organizations often filter or limit ICMP traffic to reduce information exposure.

## Common Uses

- Ping
- Traceroute
- Network diagnostics
- Connectivity testing
- Error reporting

## Best Practices

- Allow only the ICMP traffic your environment requires.
- Monitor ICMP activity for reconnaissance attempts.
- Understand common ICMP message types used during troubleshooting.

## Related Labs & Projects

- Ping Lab
- Traceroute Lab
- Wireshark ICMP Analysis
