# tcpdump

## Overview

`tcpdump` is a command-line packet capture and network analysis tool used to inspect network traffic in real time or from saved packet capture (PCAP) files. It captures packets directly from a network interface using the libpcap library and is commonly used for network troubleshooting, protocol analysis, security investigations, and incident response.

## Core Capabilities

- Capture live network traffic
- Read and analyze existing PCAP files
- Filter packets using Berkeley Packet Filter (BPF) syntax
- Display packet headers and protocol information
- Capture traffic from specific interfaces
- Save captures for later analysis in Wireshark or other tools
- Troubleshoot connectivity and network performance issues
- Investigate suspicious or malicious network activity

## Common Uses

- Diagnosing network connectivity problems
- Verifying client-server communication
- Monitoring DNS, HTTP, HTTPS, SSH, and other protocols
- Capturing packets during penetration tests
- Investigating malware or attacker network activity
- Collecting evidence during incident response
- Creating packet captures for later analysis in Wireshark

## Important Commands or Workflow

### List available interfaces

```bash
tcpdump -D
```

### Capture packets on an interface

```bash
sudo tcpdump -i eth0
```

### Capture a limited number of packets

```bash
sudo tcpdump -i eth0 -c 100
```

### Save packets to a PCAP file

```bash
sudo tcpdump -i eth0 -w capture.pcap
```

### Read a saved PCAP file

```bash
tcpdump -r capture.pcap
```

### Capture only traffic for a specific host

```bash
sudo tcpdump host 192.168.1.10
```

### Capture traffic on a specific port

```bash
sudo tcpdump port 443
```

### Capture only TCP traffic

```bash
sudo tcpdump tcp
```

### Capture only UDP traffic

```bash
sudo tcpdump udp
```

### Increase output detail

```bash
sudo tcpdump -vv
```

### Disable hostname resolution

```bash
sudo tcpdump -n
```

### Typical workflow

1. Identify the correct network interface.
2. Start a capture with appropriate filters.
3. Observe traffic or save it to a PCAP file.
4. Stop the capture when enough data has been collected.
5. Analyze the output directly or open the PCAP in Wireshark.

## Best Practices

- Use capture filters to reduce unnecessary traffic.
- Disable name resolution (`-n`) for faster and cleaner output.
- Save important captures as PCAP files for later analysis.
- Limit capture duration or packet count when possible.
- Run with administrative privileges only when necessary.
- Capture only the traffic needed to minimize storage and analysis time.
- Use Wireshark for deeper protocol analysis after collecting packets.

## Limitations

- Requires elevated privileges for live packet capture on most systems.
- Encrypted traffic (such as HTTPS) cannot be decrypted without the necessary keys.
- Capturing on busy networks can generate very large files.
- Incorrect filters may miss important traffic.
- Primarily a packet capture tool; it provides less visualization than GUI tools like Wireshark.
