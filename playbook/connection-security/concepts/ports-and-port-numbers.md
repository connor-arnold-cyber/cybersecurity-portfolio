# Ports and Port Numbers

## Overview

Ports identify the service or application receiving network traffic on a device. While an IP address identifies the host, a port identifies the specific process or service. Security professionals constantly use port numbers during troubleshooting, firewall configuration, packet analysis, and penetration testing.

---

## Why It Matters

Knowing common ports allows you to:

- Identify running services
- Recognize suspicious network activity
- Interpret packet captures
- Configure firewall rules
- Perform port scanning
- Troubleshoot connectivity issues

---

## Common Ports

| Port | Protocol | Service | Secure? | Notes |
|------:|:--------:|---------|:-------:|-------|
| 20 | TCP | FTP (Data) | ❌ | FTP data transfer |
| 21 | TCP | FTP (Control) | ❌ | FTP commands |
| 22 | TCP | SSH | ✅ | Secure remote administration |
| 23 | TCP | Telnet | ❌ | Insecure remote administration |
| 25 | TCP | SMTP | ❌ | Mail transfer |
| 53 | TCP/UDP | DNS | ⚠️ | UDP for queries, TCP for zone transfers |
| 67 | UDP | DHCP Server | — | Assigns IP addresses |
| 68 | UDP | DHCP Client | — | Receives IP addresses |
| 69 | UDP | TFTP | ❌ | Simple file transfers |
| 80 | TCP | HTTP | ❌ | Web traffic |
| 88 | TCP/UDP | Kerberos | ✅ | Active Directory authentication |
| 110 | TCP | POP3 | ❌ | Email retrieval |
| 123 | UDP | NTP | — | Time synchronization |
| 137 | UDP | NetBIOS Name Service | ❌ | Legacy Windows networking |
| 138 | UDP | NetBIOS Datagram | ❌ | Legacy Windows networking |
| 139 | TCP | NetBIOS Session | ❌ | File and printer sharing |
| 143 | TCP | IMAP | ❌ | Email retrieval |
| 161 | UDP | SNMP | ⚠️ | Network management |
| 162 | UDP | SNMP Trap | ⚠️ | SNMP alerts |
| 389 | TCP/UDP | LDAP | ❌ | Directory services |
| 443 | TCP | HTTPS | ✅ | Secure web traffic |
| 445 | TCP | SMB | ⚠️ | Windows file sharing |
| 465 | TCP | SMTPS | ✅ | Secure SMTP |
| 514 | UDP | Syslog | — | Log forwarding |
| 587 | TCP | SMTP Submission | ✅ | Authenticated email sending |
| 636 | TCP | LDAPS | ✅ | Secure LDAP |
| 993 | TCP | IMAPS | ✅ | Secure IMAP |
| 995 | TCP | POP3S | ✅ | Secure POP3 |
| 1433 | TCP | Microsoft SQL Server | — | SQL Server |
| 1521 | TCP | Oracle Database | — | Oracle listener |
| 3306 | TCP | MySQL | — | MySQL database |
| 3389 | TCP | Remote Desktop (RDP) | ⚠️ | Remote Windows administration |
| 5432 | TCP | PostgreSQL | — | PostgreSQL database |
| 5900 | TCP | VNC | ⚠️ | Remote desktop |
| 8080 | TCP | HTTP Alternate | — | Web proxies & development servers |

---

## Ports Worth Memorizing

These are the ports almost every cybersecurity professional should know by memory:

- 20/21 — FTP
- 22 — SSH
- 23 — Telnet
- 25 — SMTP
- 53 — DNS
- 67/68 — DHCP
- 69 — TFTP
- 80 — HTTP
- 88 — Kerberos
- 110 — POP3
- 123 — NTP
- 139 — NetBIOS
- 143 — IMAP
- 161/162 — SNMP
- 389 — LDAP
- 443 — HTTPS
- 445 — SMB
- 587 — SMTP Submission
- 636 — LDAPS
- 993 — IMAPS
- 995 — POP3S
- 1433 — MSSQL
- 3306 — MySQL
- 3389 — RDP
- 5432 — PostgreSQL
- 5900 — VNC
- 8080 — HTTP Alternate

---

## Security Notes

- Prefer encrypted protocols whenever possible.
- Disable services you don't use.
- Never expose management services (SSH, RDP, VNC, database ports) directly to the Internet unless absolutely necessary.
- Unexpected open ports often indicate misconfiguration or compromise.
- Port scanning is one of the first steps in penetration testing and incident response.

---

## Related Labs & Projects

- Nmap Port Scanning
- Service Enumeration
- Firewall Rule Analysis
- Wireshark Traffic Analysis
