# Terminal Access Controller Access-Control System Plus (TACACS+)

## Overview

Terminal Access Controller Access-Control System Plus (TACACS+) is a centralized Authentication, Authorization, and Accounting (AAA) protocol primarily used to control administrative access to network devices.

Unlike RADIUS, which is commonly used for network access authentication, TACACS+ is designed to provide detailed control and auditing of administrator actions on devices such as routers, switches, and firewalls.

## Key Concepts

### Centralized Authentication

TACACS+ allows multiple network devices to authenticate administrators through a central server.

Instead of maintaining administrator accounts on every device, authentication requests are sent to the TACACS+ server.

### AAA

TACACS+ fully supports all three components of AAA:

- **Authentication** – Verifies the administrator's identity.
- **Authorization** – Determines which commands or actions are permitted.
- **Accounting** – Records commands executed and administrative activity.

### Command Authorization

One of TACACS+'s strongest features is granular command authorization.

Organizations can specify exactly which commands an administrator is allowed to execute.

For example:

- One administrator may only view configurations.
- Another may modify interface settings.
- A senior administrator may have full administrative privileges.

### Full Packet Encryption

TACACS+ encrypts the entire authentication packet between the client and server.

This provides stronger protection for authentication information and authorization data compared to protocols that encrypt only portions of the communication.

### Client and Server

A TACACS+ deployment consists of:

- **TACACS+ Client** – A network device requesting authentication.
- **TACACS+ Server** – Verifies credentials and returns authentication and authorization decisions.

The client relies on the TACACS+ server to determine whether administrative access should be granted.

## TACACS+ vs. RADIUS

| TACACS+ | RADIUS |
|----------|---------|
| Primarily used for device administration | Primarily used for user network access |
| Encrypts the entire packet | Encrypts only the user's password |
| Supports per-command authorization | Limited command authorization |
| Common on routers, switches, and firewalls | Common for VPNs, Wi-Fi, and remote access |

## Why It Matters

TACACS+ provides centralized management of administrator accounts while allowing organizations to control exactly what administrators can do on critical network infrastructure. Its detailed authorization and accounting capabilities make it a common choice for securing enterprise network administration.

## Common Uses

- Router administration
- Switch administration
- Firewall administration
- Network infrastructure management
- Enterprise AAA
- Administrative auditing
- Privileged access management

## Best Practices

- Use TACACS+ for administrative access to network devices.
- Apply the Principle of Least Privilege through command authorization.
- Enable accounting to record all administrative actions.
- Protect TACACS+ servers because they control privileged access.
- Regularly review authentication and accounting logs for suspicious activity.
