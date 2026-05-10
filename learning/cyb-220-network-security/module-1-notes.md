# Module 1 Notes – CYB 220 Network Security

## Systems Thinking

Systems thinking is a way of looking at problems as part of a larger interconnected system rather than isolated events.

### Main Idea

- Focus on root causes instead of symptoms.
- Look for patterns over time.
- Understand how different parts of a system affect one another.
- Small changes in the right place can create major improvements.

### When to Use Systems Thinking

- The problem is important.
- The issue keeps happening.
- Previous attempts to fix it have failed.
- Multiple people or departments are involved.

### Key Takeaway

> Step back, look at the bigger picture, and identify the underlying causes before taking action.

---

## Incident Mitigation Techniques (CompTIA Security+ Objective 4.4)

After a security incident is stabilized, the security team should:

1. Identify what happened.
2. Contain the threat.
3. Fix vulnerabilities.
4. Reconfigure security controls.
5. Update incident response procedures.
6. Prevent the same attack from happening again.

---

## Application Approved List (Allow List)

A list of software that is explicitly allowed to run.

### Key Idea

If the application is not on the list, it cannot run.

### Benefits

- Prevents unauthorized software.
- Stops many malware infections.
- Provides stronger security than a block list.

---

## Application Block List (Deny List)

A list of software that is explicitly prohibited.

### Key Idea

Known bad applications are blocked.

### Weakness

Attackers can rename or modify malware to bypass the list.

---

## Quarantine

Moves suspicious files to a safe location where they cannot execute.

### Purpose

- Prevents malware from running.
- Preserves files for forensic analysis.
- Helps improve future detection rules.

### Microsoft Defender Quarantine Location

```text
C:\ProgramData\Microsoft\Windows Defender\Quarantine
```

---

## Configuration Changes

Security incidents often reveal weak settings.

### Examples

- Open ports
- Weak passwords
- Excessive permissions
- Disabled logging

### Goal

Harden systems by correcting insecure configurations.

---

## Firewall Rules

Firewalls allow or block network traffic based on defined rules.

### Trusted Zone

Internal network.

### Least-Trusted Zone

The internet and external users.

### Post-Incident Actions

- Block malicious IP addresses.
- Close unnecessary ports.
- Restrict protocols.
- Apply least privilege.
- Follow zero trust principles.

---

## MDM (Mobile Device Management)

Used to manage and secure laptops, phones, tablets, and BYOD devices.

### Capabilities

- Push security policies
- Install applications
- Track devices
- Remote wipe lost devices
- Enforce compliance settings

---

## DLP (Data Loss Prevention)

Prevents sensitive information from leaving the organization.

### Protects

- Customer data
- Financial records
- Intellectual property
- Personal information

### Controls

- Block USB transfers
- Monitor email attachments
- Detect cloud uploads
- Alert on suspicious activity

---

## Content Filter / URL Filter

Blocks access to dangerous or inappropriate websites.

### Examples

- Phishing sites
- Malware-hosting pages
- Adult content
- Gambling websites

---

## Update or Revoke Certificates

Digital certificates should be revoked if compromised, lost, or stolen.

### CRL (Certificate Revocation List)

A list of certificates that are no longer trusted.

---

## Isolation

Separates a compromised system from the network while preserving evidence.

### Purpose

- Prevent further spread
- Allow forensic analysis
- Protect critical data

---

## Containment

Stops the overall incident from spreading to other systems.

### Actions

- Disconnect infected devices
- Reset passwords
- Disable suspicious accounts
- Preserve evidence

### Difference from Isolation

- Isolation = One affected host
- Containment = Broader response strategy

---

## Segmentation

Divides a network into smaller zones or subnets.

### Technologies Used

- VLANs
- Firewalls
- Access Control Lists (ACLs)

### Benefits

- Limits lateral movement
- Improves performance
- Supports compliance
- Protects high-value assets

---

## SOAR

Security Orchestration, Automation, and Response.

### Purpose

Automates repetitive security tasks and integrates multiple security tools.

### Examples

- Analyze alerts
- Assign severity
- Notify analysts
- Quarantine endpoints
- Open tickets

---

## Runbooks

Detailed workflows, often automated, that define the exact steps to perform.

### Example

1. Receive malware alert
2. Check file hash
3. Query VirusTotal
4. Isolate endpoint
5. Notify analysts

---

## Playbooks

Step-by-step response procedures for specific incident types.

### Examples

- Phishing response
- Ransomware response
- Insider threat response

---

## Runbook vs Playbook

| Term | Meaning |
|------|---------|
| Runbook | Operational workflow, usually automated |
| Playbook | Incident-specific response checklist |

---

## Key Terms

| Term | Definition |
|------|------------|
| Allow List | Only approved software may run |
| Deny List | Known bad software is blocked |
| Quarantine | Safe storage for suspicious files |
| DLP | Prevents unauthorized data transfer |
| Isolation | Separates one infected system |
| Containment | Stops the spread of an incident |
| Segmentation | Divides the network into security zones |
| SOAR | Automates security operations |
| Runbook | Detailed workflow of actions |
| Playbook | Structured incident response checklist |

---

## Quick Memory Tricks

- Allow List = Allow Only
- DLP = Don't Let it Pass
- Isolation = One Host
- Containment = Whole Incident
- Segmentation = Divide and Protect
- SOAR = Security Automation
- Runbook = Robot Steps
- Playbook = Team Strategy

---

## Bottom Line

This module focused on how organizations respond after a cybersecurity incident.

The goal is to:

- Lock down affected systems
- Prevent data loss
- Contain the attack
- Automate future responses
- Strengthen defenses so the same incident does not happen again

> Good incident response is not just about cleaning up after an attack. It is about learning from the incident and building a stronger security posture.
