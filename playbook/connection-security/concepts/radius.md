# Remote Authentication Dial-In User Service (RADIUS)

## Overview

Remote Authentication Dial-In User Service (RADIUS) is a centralized Authentication, Authorization, and Accounting (AAA) protocol used to manage network access for users and devices.

Instead of storing user accounts on every network device, authentication requests are sent to a central RADIUS server, providing consistent security policies across the network.

## Key Concepts

### Centralized Authentication

RADIUS allows multiple network devices to use a single authentication server.

Devices that commonly use RADIUS include:

- Wireless access points
- VPN servers
- Network switches
- Routers
- Firewalls

This centralizes user management and simplifies administration.

### AAA

RADIUS provides all three components of AAA:

- **Authentication** – Verifies a user's identity.
- **Authorization** – Determines the services or resources the user may access.
- **Accounting** – Records login sessions and user activity.

### Client and Server

A RADIUS deployment consists of:

- **RADIUS Client (Network Access Server/NAS)** – Receives the user's credentials and forwards them to the RADIUS server.
- **RADIUS Server** – Verifies the credentials and returns an access decision.

The client does not perform authentication itself—it relies on the RADIUS server.

### Shared Secret

Communication between the RADIUS client and server is protected using a shared secret.

Both systems must be configured with the same secret to communicate successfully.

The shared secret is **not** the user's password.

### Authentication Flow

A simplified RADIUS authentication process is:

1. A user attempts to connect to a network device.
2. The device sends the credentials to the RADIUS server.
3. The RADIUS server verifies the credentials.
4. The server returns an Access-Accept or Access-Reject response.
5. If accepted, the user is granted access based on the configured authorization policies.

## RADIUS vs. Local Authentication

| Local Authentication | RADIUS |
|----------------------|---------|
| Accounts stored on each device | Accounts stored centrally |
| Managed individually | Managed from one server |
| Difficult to scale | Scales easily across many devices |
| Limited auditing | Supports centralized accounting |

## Why It Matters

RADIUS simplifies identity management in enterprise networks by centralizing authentication and authorization. It allows organizations to enforce consistent security policies, monitor user activity, and manage access across many devices from a single location.

## Common Uses

- Enterprise Wi-Fi (802.1X)
- VPN authentication
- Network device administration
- Switch authentication
- Router authentication
- Remote access services
- NAC (Network Access Control)

## Best Practices

- Use strong shared secrets between RADIUS clients and servers.
- Protect RADIUS traffic with secure network designs or additional encryption when appropriate.
- Enable accounting to maintain audit logs.
- Integrate RADIUS with centralized directory services when possible.
- Monitor authentication logs for suspicious activity.
