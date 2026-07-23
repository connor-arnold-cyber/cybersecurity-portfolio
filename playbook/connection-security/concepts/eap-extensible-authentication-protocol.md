# Extensible Authentication Protocol (EAP)

## Overview

Extensible Authentication Protocol (EAP) is an authentication framework used by IEEE 802.1X to support multiple authentication methods. Rather than being a single authentication protocol, EAP provides a standard way to transport authentication information between a client and an authentication server.

EAP is commonly used to authenticate users and devices on wired and wireless enterprise networks.

## Key Concepts

### Authentication Framework

EAP does not define a single authentication method.

Instead, it provides a framework that supports many authentication methods, known as **EAP methods**.

This flexibility allows organizations to choose the authentication method that best meets their security requirements.

### EAP Participants

An EAP authentication process typically involves three components:

| Component | Purpose |
|----------|---------|
| **Supplicant** | The client requesting network access |
| **Authenticator** | The switch or wireless access point controlling access |
| **Authentication Server** | Usually a RADIUS server that validates credentials |

The authenticator forwards EAP messages between the client and the authentication server.

### Common EAP Methods

Several EAP methods are widely used:

| Method | Description |
|--------|-------------|
| **EAP-TLS** | Uses client and server digital certificates for mutual authentication. Considered one of the most secure methods. |
| **PEAP (Protected EAP)** | Creates an encrypted TLS tunnel before authenticating the user, typically with a username and password. |
| **EAP-TTLS** | Similar to PEAP but supports additional authentication mechanisms inside the encrypted tunnel. |
| **EAP-FAST** | Cisco-developed method that uses Protected Access Credentials (PACs) instead of certificates. |

### Mutual Authentication

Many EAP methods support mutual authentication.

This means:

- The client verifies the identity of the authentication server.
- The server verifies the identity of the client.

Mutual authentication helps prevent impersonation and man-in-the-middle attacks.

### Secure Credential Exchange

Many EAP methods encrypt authentication traffic, preventing attackers from capturing usernames, passwords, or other sensitive credentials during the authentication process.

## EAP vs. 802.1X

| EAP | IEEE 802.1X |
|-----|-------------|
| Authentication framework | Network access control standard |
| Defines authentication methods | Controls network access |
| Supports multiple EAP methods | Uses EAP during authentication |
| Verifies user or device identity | Grants or denies network access |

## Why It Matters

EAP allows organizations to use strong, flexible authentication methods without changing the underlying 802.1X infrastructure. It is a foundational technology for secure enterprise wired and wireless authentication.

## Common Uses

- Enterprise Wi-Fi
- Wired enterprise networks
- 802.1X authentication
- RADIUS authentication
- Network Access Control (NAC)
- University networks
- Corporate environments

## Best Practices

- Prefer certificate-based methods such as EAP-TLS when possible.
- Avoid weak or legacy authentication methods.
- Protect authentication servers with strong security controls.
- Use HTTPS and secure certificate management where applicable.
- Combine EAP with Multi-Factor Authentication (MFA) when supported.
