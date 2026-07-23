# Intrusion Detection System (IDS)

## Overview

An Intrusion Detection System (IDS) is a security system that monitors network or host activity for signs of malicious behavior, policy violations, or known attack patterns. Unlike a firewall, an IDS does not block traffic. Instead, it detects suspicious activity and generates alerts so security personnel can investigate.

IDS solutions are commonly deployed as part of a layered defense strategy.

## Key Concepts

### Detection

An IDS continuously monitors traffic or system activity for indicators of compromise.

It compares observed activity against detection methods such as:

- Known attack signatures
- Suspicious behavior
- Security policies

When suspicious activity is detected, the IDS generates an alert.

### Signature-Based Detection

Signature-based detection compares activity against a database of known attack patterns.

Advantages:

- Accurate for known attacks
- Low false positive rate

Limitations:

- Cannot detect previously unknown threats
- Requires regular signature updates

### Anomaly-Based Detection

Anomaly-based detection establishes a baseline of normal activity and alerts when behavior significantly deviates from that baseline.

Advantages:

- Can identify previously unknown attacks
- Detects unusual behavior

Limitations:

- May generate more false positives
- Requires time to establish normal activity

### Network IDS (NIDS)

A Network Intrusion Detection System monitors traffic flowing across a network.

It is typically placed at strategic points where it can observe communications between devices.

### Host IDS (HIDS)

A Host Intrusion Detection System monitors activity on an individual system.

It can detect events such as:

- File modifications
- Unauthorized logins
- Suspicious processes
- System configuration changes

## Why It Matters

An IDS provides visibility into suspicious activity that may bypass preventive controls. By generating timely alerts, it helps security teams detect attacks early and begin incident response before significant damage occurs.

## Common Uses

- Detect network attacks
- Monitor suspicious activity
- Identify policy violations
- Support incident response
- Monitor critical servers
- Investigate security events

## Best Practices

- Keep detection signatures updated.
- Tune detection rules to reduce false positives.
- Monitor IDS alerts regularly.
- Investigate high-severity alerts promptly.
- Integrate IDS alerts with SIEM platforms when possible.
- Use IDS alongside firewalls and other preventive security controls.
