# Man-in-the-Middle (MitM) Attack

## Overview

A Man-in-the-Middle (MitM) attack occurs when an attacker secretly intercepts and possibly alters communications between two parties without either party realizing it.

Instead of communicating directly with each other, both parties unknowingly communicate through the attacker.

## Key Concepts

### Interception

The attacker positions themselves between two communicating systems.

The communication flow becomes:

```text
Client → Attacker → Server
       ←          ←
```

The attacker can observe, modify, inject, or block traffic before forwarding it.

### Eavesdropping

A MitM attacker can passively monitor network traffic to collect sensitive information such as:

- Usernames
- Passwords
- Session cookies
- Credit card numbers
- Personal information

If the traffic is encrypted properly, the attacker may capture the data but typically cannot read its contents.

### Data Manipulation

Some MitM attacks actively modify communications.

Examples include:

- Changing downloaded files
- Redirecting users to malicious websites
- Altering financial transactions
- Injecting malicious code into web pages

### Common Techniques

MitM attacks can be carried out using several methods, including:

- ARP spoofing
- DNS spoofing
- Rogue Wi-Fi access points
- Session hijacking
- SSL stripping
- Evil Twin attacks

These techniques allow attackers to redirect or intercept network traffic.

### Prevention

Several technologies help defend against MitM attacks:

- HTTPS
- TLS
- VPNs
- Digital certificates
- Certificate validation
- Multi-Factor Authentication (MFA)

Users should also avoid connecting to untrusted public Wi-Fi networks without protection.

## Why It Matters

MitM attacks threaten the confidentiality and integrity of communications. They can lead to credential theft, financial fraud, malware delivery, and unauthorized access to sensitive systems.

Understanding MitM attacks helps security professionals recognize why encryption, authentication, and certificate validation are essential.

## Common Uses

MitM attacks are commonly discussed in relation to:

- Public Wi-Fi attacks
- Credential theft
- Session hijacking
- Network penetration testing
- Web application security
- Incident response investigations

## Best Practices

- Always use HTTPS instead of HTTP.
- Verify certificate warnings rather than ignoring them.
- Use VPNs when connecting over untrusted networks.
- Enable Multi-Factor Authentication (MFA).
- Keep systems and browsers updated.
- Avoid connecting to unknown or suspicious wireless networks.
