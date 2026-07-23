# Nessus

## Overview

Nessus is a commercial vulnerability scanner developed by Tenable. It automates the process of identifying known vulnerabilities, missing patches, insecure configurations, and exposed services on systems and networks.

Nessus is one of the most widely used vulnerability scanners in enterprise environments.

## Key Concepts

### Plugin-Based Detection

Nessus uses a large collection of plugins to check for known vulnerabilities and security issues.

Regular plugin updates allow Nessus to detect newly discovered vulnerabilities.

### Authenticated Scanning

Nessus can log into target systems using authorized credentials to perform a deeper assessment.

Authenticated scans typically identify:

- Missing security patches
- Installed software
- Security configuration issues
- Weak system settings

### Unauthenticated Scanning

Without credentials, Nessus evaluates systems from an external perspective.

It can identify:

- Open ports
- Running services
- Publicly exposed software
- Some remotely detectable vulnerabilities

### Scan Results

A typical Nessus report includes:

- Host information
- Open ports
- Running services
- Vulnerability severity
- CVE identifiers
- Descriptions
- Recommended remediation

## Why It Matters

Nessus helps organizations identify security weaknesses before attackers can exploit them. It supports vulnerability management, patch management, compliance, and security assessments.

## Common Uses

- Internal vulnerability assessments
- External vulnerability assessments
- Patch verification
- Configuration auditing
- Compliance scanning
- Security baselines
- Risk assessment

## Best Practices

- Scan only systems you are authorized to assess.
- Keep plugins updated.
- Use authenticated scans whenever possible.
- Review findings before remediation.
- Validate critical findings manually.
- Rescan systems after applying fixes.
