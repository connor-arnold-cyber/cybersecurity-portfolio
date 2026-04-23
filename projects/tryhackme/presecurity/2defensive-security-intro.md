# TryHackMe - Defensive Security Intro

## What I Learned

Defensive security is about:
- Preventing attacks
- Detecting attacks
- Responding to attacks

This is handled by the **Blue Team**.

---

## Prevention

Goal: stop attacks before they happen

Examples:
- Security awareness training (don’t click dumb stuff)
- Asset management (know what systems you have)
- Patching (fix known vulnerabilities)

Tools:
- Firewall → filters traffic (IP, port, protocol)
- IPS → inspects traffic and blocks threats

---

## Detection & Monitoring

Systems constantly generate logs.

Process:
1. Traffic hits network
2. Firewall allows or blocks it
3. IPS checks for threats
4. Logs record activity
5. SIEM analyzes everything

---

## SOC (Security Operations Center)

SOC = team that monitors for threats

They look for:
- Vulnerabilities
- Policy violations
- Unauthorized access
- Network intrusions

---

## SIEM (Important Tool)

SIEM:
- Collects logs from multiple systems
- Analyzes them
- Generates alerts

SOC analysts:
- Investigate alerts
- Look for patterns
- Decide if it's actually malicious

---

## DFIR (Incident Response + Forensics)

Digital Forensics:
- Analyzing evidence from attacks

Evidence sources:
- Logs
- Memory (RAM)
- File system

Incident Response Phases:
1. Preparation
2. Detection & Analysis
3. Containment, Eradication, Recovery
4. Review

---

## Malware Basics

Types:
- Virus → spreads and damages files
- Trojan → disguises itself
- Ransomware → locks files for money

Analysis:
- Static → don’t run it
- Dynamic → run it safely in a VM

---

## Real-World Takeaways

- You should assume breaches WILL happen
- Prevention alone is not enough
- Logs are everything in detection
- Attackers always leave traces
