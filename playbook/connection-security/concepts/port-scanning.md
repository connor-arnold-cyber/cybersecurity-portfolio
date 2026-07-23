# Port Scanning

## Overview

Port scanning is the process of sending network probes to a target to determine which ports are open, closed, or filtered. It is used during network troubleshooting, vulnerability assessment, and penetration testing to identify reachable services.

An open port does not automatically indicate a vulnerability. It indicates that a service is listening and may require further investigation.

## Key Concepts

### Port States

- **Open:** A service is listening and accepting connections.
- **Closed:** The host is reachable, but no service is listening on the port.
- **Filtered:** A firewall or other device prevents the scanner from determining the port state.
- **Open|Filtered:** The scanner cannot determine whether the port is open or filtered.
- **Unfiltered:** The port is reachable, but the scan cannot determine whether it is open or closed.

### Common Scan Types

| Scan | Behavior | Primary Purpose |
|------|----------|-----------------|
| TCP Connect | Completes the full TCP handshake | Reliable TCP scanning |
| SYN | Sends SYN but does not complete the handshake | Fast TCP scanning |
| UDP | Sends UDP probes | Discover UDP services |
| ACK | Tests whether traffic is filtered | Firewall rule analysis |
| FIN | Sends a packet with the FIN flag | Infer port state from TCP behavior |
| NULL | Sends a packet with no TCP flags | Infer port state from TCP behavior |
| Xmas | Sends FIN, PSH, and URG flags | Infer port state from TCP behavior |

FIN, NULL, and Xmas scans work best against systems that follow standard TCP behavior. Results may be unreliable against Windows systems and some network devices.

### TCP Scan Responses

For a SYN scan:

- **SYN/ACK:** The port is open.
- **RST:** The port is closed.
- **No response or ICMP error:** The port is probably filtered.

For FIN, NULL, and Xmas scans:

- **No response:** The port may be open or filtered.
- **RST:** The port is closed.

For an ACK scan:

- **RST:** The port is unfiltered.
- **No response or ICMP error:** The port is filtered.

ACK scans determine firewall filtering, not whether a service is listening.

### UDP Scanning

UDP does not use a handshake, making UDP scans slower and less certain than TCP scans.

Common responses include:

- **UDP response:** The port is open.
- **ICMP Port Unreachable:** The port is closed.
- **No response:** The port may be open or filtered.

Common UDP services include DNS, DHCP, NTP, and SNMP.

## Why It Matters

Port scanning reveals a system's exposed network services and overall attack surface. Security professionals use the results to locate unnecessary services, identify possible misconfigurations, prioritize vulnerability testing, and verify firewall rules.

## Common Uses

- Discover open TCP and UDP ports
- Identify exposed network services
- Map reachable systems
- Verify firewall behavior
- Support service enumeration
- Confirm that unused ports are closed
- Prepare for vulnerability scanning
- Troubleshoot network connectivity

## Best Practices

- Scan only systems you own or are authorized to test.
- Confirm the target IP address and network range before scanning.
- Begin with host discovery when appropriate.
- Scan TCP and UDP separately because they behave differently.
- Use service detection to investigate open ports.
- Remember that firewalls can produce incomplete or misleading results.
- Save scan results for documentation and comparison.
- Validate important findings with another tool or manual testing.
- Do not assume that a default port always runs its expected service.
