# Accounting

## Overview

Accounting is the process of recording and monitoring user and system activity after authentication and authorization have occurred. It provides an audit trail that shows who accessed a system, what actions were performed, and when those actions took place.

Accounting is the third component of the **AAA (Authentication, Authorization, and Accounting)** security model.

## Key Concepts

### Activity Logging

Accounting records events that occur during a user's session.

Common logged information includes:

- Login and logout times
- Commands executed
- Files accessed
- Configuration changes
- Network connections
- Administrative actions

### Audit Trail

The collected records create an audit trail.

An audit trail allows administrators and investigators to reconstruct events, identify suspicious activity, and determine responsibility for specific actions.

### Accountability

Because user activity is logged, individuals can be held accountable for their actions.

This discourages misuse and supports internal investigations.

### Monitoring

Accounting data can be monitored in real time or reviewed later.

Organizations often forward logs to centralized logging or SIEM systems for analysis and alerting.

### AAA

Accounting works alongside the other components of AAA:

- **Authentication** – Verifies identity.
- **Authorization** – Determines permissions.
- **Accounting** – Records activity.

Together, these components provide a complete framework for access control and auditing.

## Why It Matters

Without accounting, organizations would have little visibility into what users and systems are doing after access is granted. Logging and auditing are essential for detecting attacks, investigating security incidents, demonstrating regulatory compliance, and troubleshooting operational problems.

## Common Uses

- Security auditing
- Compliance reporting
- Incident response
- User activity monitoring
- Network device logging
- System administration
- SIEM platforms

## Best Practices

- Enable logging on critical systems and network devices.
- Synchronize system clocks using NTP to ensure accurate timestamps.
- Protect logs from unauthorized modification or deletion.
- Regularly review logs for suspicious activity.
- Retain logs according to organizational and regulatory requirements.
