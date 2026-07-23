# Kerberos

## Overview

Kerberos is a network authentication protocol that securely verifies the identity of users and services without transmitting passwords across the network. It uses symmetric-key cryptography and a trusted third party called the **Key Distribution Center (KDC)** to authenticate users.

Kerberos is the default authentication protocol used in Microsoft Active Directory environments.

## Key Concepts

### Key Distribution Center (KDC)

The Key Distribution Center is the trusted authority in a Kerberos environment.

The KDC consists of two logical services:

- **Authentication Server (AS)** – Verifies the user's identity.
- **Ticket Granting Server (TGS)** – Issues tickets that allow access to network services.

### Tickets

Instead of repeatedly sending passwords, Kerberos uses tickets.

A ticket proves that a user has already been authenticated and is authorized to request access to specific services.

This reduces password exposure across the network.

### Ticket Granting Ticket (TGT)

After a successful login, the KDC issues a **Ticket Granting Ticket (TGT)**.

The TGT allows the user to request additional service tickets without entering their password again until the TGT expires.

### Service Tickets

When a user attempts to access a network resource, the TGS issues a **service ticket** for that specific service.

The service validates the ticket before granting access.

### Mutual Authentication

Kerberos supports **mutual authentication**.

This means:

- The client verifies the server.
- The server verifies the client.

Both parties confirm each other's identity before communication continues.

## Authentication Process

A simplified Kerberos authentication flow is:

1. The user logs in.
2. The Authentication Server verifies the user's credentials.
3. The KDC issues a Ticket Granting Ticket (TGT).
4. The user requests a service ticket from the Ticket Granting Server.
5. The TGS issues a service ticket.
6. The user presents the service ticket to the requested service.
7. The service validates the ticket and grants access.

## Why It Matters

Kerberos provides secure authentication without repeatedly transmitting passwords across the network. It supports Single Sign-On (SSO), mutual authentication, and centralized identity management, making it one of the most widely deployed enterprise authentication protocols.

## Common Uses

- Microsoft Active Directory
- Windows domain authentication
- Enterprise networks
- Single Sign-On (SSO)
- File servers
- Print servers
- Internal business applications

## Best Practices

- Synchronize system clocks using NTP, as Kerberos is sensitive to time differences.
- Protect the Key Distribution Center because it is a critical component of the authentication system.
- Use strong passwords to protect Kerberos accounts.
- Monitor for suspicious ticket activity.
- Keep domain controllers and Kerberos services updated.
