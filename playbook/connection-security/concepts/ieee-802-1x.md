# IEEE 802.1X

## Overview

IEEE 802.1X is a network access control (NAC) standard that authenticates users and devices before allowing them to connect to a wired or wireless network.

Rather than granting immediate network access, 802.1X requires successful authentication through an authentication server, helping prevent unauthorized devices from joining the network.

## Key Concepts

### The Three Components

802.1X authentication involves three primary components:

| Component | Purpose |
|-----------|---------|
| **Supplicant** | The client device requesting network access |
| **Authenticator** | The network device controlling access (switch or wireless access point) |
| **Authentication Server** | Verifies credentials, typically a RADIUS server |

### Authentication Process

A simplified 802.1X authentication flow is:

1. A device connects to the network.
2. The switch or access point blocks normal network traffic.
3. The device provides authentication credentials.
4. The authenticator forwards the credentials to the authentication server.
5. The authentication server approves or denies the request.
6. If approved, normal network access is granted.

### Extensible Authentication Protocol (EAP)

802.1X uses the Extensible Authentication Protocol (EAP) to transport authentication information.

Different EAP methods support various authentication mechanisms, including:

- Passwords
- Digital certificates
- Smart cards
- Multi-Factor Authentication (MFA)

### Port-Based Access Control

802.1X is often called **port-based network access control** because each switch port or wireless connection remains blocked until authentication succeeds.

Once authenticated, the port transitions into an authorized state.

### Dynamic Authorization

After successful authentication, organizations may dynamically assign:

- VLANs
- Access Control Lists (ACLs)
- Security policies
- User permissions

This allows different users to receive different levels of network access.

## Why It Matters

802.1X prevents unauthorized users and devices from connecting to enterprise networks. It is a core component of modern Network Access Control (NAC) solutions and significantly improves network security by requiring authentication before granting access.

## Common Uses

- Enterprise wired networks
- Corporate Wi-Fi
- Universities
- Healthcare organizations
- Government networks
- Bring Your Own Device (BYOD) environments

## Best Practices

- Use 802.1X for both wired and wireless networks.
- Integrate with a RADIUS authentication server.
- Prefer certificate-based authentication when possible.
- Combine with Network Access Control (NAC) for device compliance checks.
- Use strong EAP methods instead of legacy authentication mechanisms.
