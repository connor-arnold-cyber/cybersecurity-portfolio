# Nmap Scan Types

| Scan | Command | What Nmap Sends | If Port is OPEN | If Port is CLOSED | Purpose |
|------|---------|-----------------|-----------------|-------------------|---------|
| TCP Connect | `-sT` | SYN → ACK (full handshake) | Connection established | RST | Normal TCP connection |
| SYN (Stealth) | `-sS` | SYN | SYN/ACK → Nmap sends RST | RST | Most common port scan |
| UDP | `-sU` | UDP packet | Usually no response (or UDP reply) | ICMP Port Unreachable | Find UDP services |
| FIN | `-sF` | FIN | No response | RST | Bypass simple filters / fingerprinting |
| NULL | `-sN` | No flags | No response | RST | Fingerprinting |
| Xmas | `-sX` | FIN + PSH + URG | No response | RST | Fingerprinting |
| ACK | `-sA` | ACK | RST (or no response if filtered) | RST (or no response if filtered) | Detect firewall filtering |

## How to Read This Table

The **OPEN** and **CLOSED** columns show **how the target responds** after receiving the scan.

Example (SYN Scan):

```text
Nmap ------ SYN ------> Target

If OPEN:
Target ---- SYN/ACK ---> Nmap

If CLOSED:
Target ----- RST ------> Nmap
```

Nmap identifies the port state from the response.

## Quick Reference

### SYN Scan (`-sS`)
- Most common scan
- Requires raw packet privileges
- Doesn't complete the handshake

### TCP Connect (`-sT`)
- Completes the handshake
- No admin/root required
- Easy to detect

### UDP Scan (`-sU`)
- Used for UDP services
- Slower than TCP scanning

### FIN / NULL / Xmas
These send unusual TCP packets and infer port state from the response.

- **Open** → No response
- **Closed** → RST

### ACK Scan (`-sA`)
Does **not** determine whether a port is open.

It determines whether a firewall is filtering packets.

- **RST** → Unfiltered
- **No response / ICMP** → Filtered

## Memorize

- `-sS` → SYN (Stealth)
- `-sT` → TCP Connect
- `-sU` → UDP
- `-sA` → ACK (Firewall detection)
- `-sF` → FIN
- `-sN` → NULL
- `-sX` → Xmas

## Mental Model

Each scan sends a different packet and asks a different question.

- **Connect** → "Can I establish a connection?"
- **SYN** → "Would you let me connect?"
- **UDP** → "Is a UDP service listening?"
- **FIN / NULL / Xmas** → "How do you react to an unexpected packet?"
- **ACK** → "Is a firewall filtering my traffic?"
