# Lightweight Directory Access Protocol (LDAP)

## Overview

Lightweight Directory Access Protocol (LDAP) is a protocol used to access and manage directory services. A directory stores information about users, groups, computers, printers, and other network resources in a centralized database.

LDAP allows applications and systems to query this directory for information and is commonly used for authentication, authorization, and user management in enterprise environments.

## Key Concepts

### Directory Service

A directory service organizes information about network resources in a hierarchical structure.

Common objects stored in a directory include:

- Users
- Groups
- Computers
- Printers
- Servers
- Organizational Units (OUs)

Applications can search this directory to locate resources or retrieve user information.

### Centralized Management

LDAP provides a single location to manage identities and resources.

Instead of maintaining separate user databases for every application, organizations can store user accounts in one directory and allow multiple systems to reference it.

### Authentication

LDAP is commonly used to verify user credentials.

When a user attempts to log in, an application can query the LDAP directory to confirm the username and password.

LDAP itself defines how to communicate with the directory—it does not specify how passwords are protected during transmission.

### Searching the Directory

Applications can perform searches to locate directory objects based on attributes such as:

- Username
- Email address
- Department
- Group membership
- Computer name

This allows applications to quickly retrieve information about users and devices.

### Secure LDAP (LDAPS)

Standard LDAP transmits data without encryption.

To protect directory communications, organizations commonly use **LDAPS**, which encrypts LDAP traffic using TLS.

- **LDAP:** TCP port 389
- **LDAPS:** TCP port 636

## LDAP vs. Active Directory

LDAP and Active Directory are often confused but are not the same.

| LDAP | Active Directory |
|------|------------------|
| Communication protocol | Directory service developed by Microsoft |
| Defines how clients access a directory | Stores directory information |
| Can communicate with many directory services | Commonly accessed using LDAP |

## Why It Matters

LDAP enables centralized identity management across enterprise networks. It allows organizations to maintain a single directory of users and resources while enabling applications to authenticate users and retrieve directory information efficiently.

## Common Uses

- User authentication
- Enterprise directories
- Active Directory
- Email systems
- VPN authentication
- Single Sign-On (SSO)
- User and group management

## Best Practices

- Use LDAPS instead of unencrypted LDAP whenever possible.
- Restrict anonymous directory access.
- Apply the Principle of Least Privilege to directory permissions.
- Monitor directory access logs for suspicious activity.
- Keep directory services and LDAP servers updated.
