# Authentication

## Overview

Authentication is the process of verifying the identity of a user, device, application, or system before granting access to resources.

Authentication answers the question:

> "Who are you?"

It is the first step in controlling access to systems and is commonly paired with authorization and accounting (AAA).

## Key Concepts

### Identity Verification

Authentication confirms that an entity is who it claims to be.

This verification occurs before access to protected resources is granted.

### Authentication Factors

Authentication methods are commonly grouped into factors:

- **Something you know** (password, PIN)
- **Something you have** (smart card, security key, smartphone)
- **Something you are** (fingerprint, facial recognition, iris scan)

Using more than one factor provides stronger security.

### Credentials

Authentication relies on credentials such as:

- Usernames
- Passwords
- Security tokens
- Certificates
- Biometric data

The system validates these credentials before allowing access.

### Single-Factor vs. Multi-Factor Authentication

- **Single-Factor Authentication (SFA)** uses one authentication factor.
- **Multi-Factor Authentication (MFA)** requires two or more different authentication factors.

MFA significantly reduces the risk of unauthorized access if one credential is compromised.

### Authentication Protocols

Many protocols support authentication, including:

- Kerberos
- RADIUS
- TACACS+
- LDAP
- OAuth
- OpenID Connect

Each is designed for different environments and authentication needs.

## Authentication vs. Authorization

| Authentication | Authorization |
|---------------|---------------|
| Verifies identity | Determines permissions |
| Answers "Who are you?" | Answers "What are you allowed to do?" |
| Happens first | Happens after authentication |
| Validates credentials | Grants or denies access to resources |

## Why It Matters

Authentication is one of the most important security controls in any system. Without reliable authentication, unauthorized users could gain access to sensitive information, applications, and infrastructure.

Nearly every secure system begins by authenticating the user before determining what actions they are permitted to perform.

## Common Uses

- Logging into operating systems
- Web applications
- VPN access
- Cloud services
- Enterprise networks
- Remote administration
- Online banking

## Best Practices

- Require strong passwords.
- Enable Multi-Factor Authentication whenever possible.
- Protect authentication credentials from unauthorized access.
- Monitor authentication logs for suspicious activity.
- Use secure authentication protocols rather than transmitting credentials in plaintext.
