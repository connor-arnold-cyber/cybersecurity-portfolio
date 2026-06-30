# File Integrity Monitoring

## Overview

File Integrity Monitoring (FIM) detects unauthorized changes to important system files by comparing their current hash values against a known trusted baseline.

## Key Concepts

- Baseline
- Hash Values
- Integrity
- Alerts
- Tripwire
- OSSEC
- Wazuh

## Why It Matters

Attackers often modify critical system files after compromising a device. File Integrity Monitoring helps detect these changes quickly so they can be investigated.

## Common Uses

- Monitoring Operating System Files
- Detecting Malware Activity
- Detecting Unauthorized Configuration Changes
- Compliance Monitoring

## Best Practices

- Create a trusted baseline before monitoring.
- Monitor critical system files.
- Investigate unexpected hash changes immediately.
- Review alerts regularly.

## Related Concepts

- [Hashing](../data-security/hashing.md) — Generates hash values used to detect unauthorized file changes.
- System Hardening *(Coming Soon)* — Reduces the attack surface and protects critical system files.
- Intrusion Detection Systems (IDS) *(Coming Soon)* — Detect suspicious activity, including unexpected file modifications.
- Logging *(Coming Soon)* — Records security events that help investigate detected changes.
- Tripwire *(Coming Soon)* — A popular File Integrity Monitoring tool.

## Related Labs & Projects

- Coming soon.
