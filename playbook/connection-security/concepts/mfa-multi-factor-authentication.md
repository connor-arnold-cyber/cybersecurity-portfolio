# Multi-Factor Authentication (MFA)

## Overview

Multi-Factor Authentication (MFA) is a security method that requires users to provide **two or more different authentication factors** to verify their identity before gaining access to a system.

By requiring multiple independent factors, MFA significantly reduces the risk of unauthorized access if one factor is compromised.

## Key Concepts

### Authentication Factors

Authentication factors are grouped into three primary categories:

- **Something you know** – Password, PIN, or security question
- **Something you have** – Smartphone, hardware token, smart card, or security key
- **Something you are** – Fingerprint, facial recognition, iris scan, or other biometric data

MFA requires factors from at least **two different categories**.

### Two-Factor Authentication (2FA)

Two-Factor Authentication (2FA) is a type of MFA that uses exactly two authentication factors.

Examples include:

- Password + authenticator app
- Password + hardware security key
- Password + fingerprint

Because it uses two factors, 2FA is considered a subset of MFA.

### One-Time Passwords (OTPs)

Many MFA systems generate temporary verification codes called One-Time Passwords (OTPs).

These codes:

- Expire after a short period
- Can only be used once
- Help protect against replay attacks

OTPs may be delivered through authenticator apps, hardware tokens, or SMS (though SMS is generally less secure).

### Authenticator Apps

Authenticator apps generate time-based verification codes without requiring a network connection.

Common examples include:

- Google Authenticator
- Microsoft Authenticator
- Authy

Authenticator apps are generally more secure than SMS-based verification.

### Hardware Security Keys

Hardware security keys are physical devices that perform cryptographic authentication.

Examples include USB and NFC security keys that support standards such as FIDO2 and WebAuthn.

They provide strong protection against phishing attacks because authentication is tied to the legitimate website.

## Why It Matters

Passwords alone are frequently compromised through phishing, credential stuffing, malware, and data breaches. MFA provides an additional layer of security by requiring an attacker to compromise multiple independent authentication factors before gaining access.

For this reason, MFA is one of the most effective security controls organizations can implement.

## Common Uses

- Online banking
- Cloud services
- VPN access
- Enterprise applications
- Email accounts
- Administrative accounts
- Password managers

## Best Practices

- Enable MFA wherever it is available.
- Prefer authenticator apps or hardware security keys over SMS.
- Protect backup recovery codes in a secure location.
- Require MFA for administrative and privileged accounts.
- Never approve unexpected MFA requests.
