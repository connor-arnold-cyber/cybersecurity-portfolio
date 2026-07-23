# OpenVAS

## Overview

OpenVAS (Open Vulnerability Assessment System) is an open-source vulnerability scanner used to identify known security weaknesses on systems and networks.

It performs many of the same functions as commercial scanners by checking hosts against a continually updated database of known vulnerabilities.

## Key Concepts

### Feed Updates

OpenVAS relies on regularly updated vulnerability feeds to detect newly discovered security issues.

Keeping these feeds current is essential for accurate scan results.

### Authenticated Scanning

When provided with authorized credentials, OpenVAS can perform deeper inspections by examining the target system from the inside.

Authenticated scans can identify:

- Missing patches
- Installed software
- Configuration weaknesses
- Security policy issues

### Unauthenticated Scanning

Without credentials, OpenVAS evaluates only what is externally visible.

It can identify:

- Open ports
- Running services
- Public software versions
- Some remotely detectable vulnerabilities

### Scan Results

OpenVAS reports commonly include:

- Host information
- Open services
- Vulnerability severity
- CVE identifiers
- Descriptions
- Recommended remediation

## Why It Matters

OpenVAS provides organizations with a free, open-source solution for discovering known vulnerabilities and improving their security posture.

It is commonly used in home labs, educational environments, and organizations that prefer open-source security tools.

## Common Uses

- Vulnerability assessments
- Security audits
- Patch verification
- Configuration reviews
- Continuous security monitoring

## Best Practices

- Scan only authorized systems.
- Keep vulnerability feeds updated.
- Use authenticated scans whenever possible.
- Validate important findings before remediation.
- Rescan systems after applying fixes.
