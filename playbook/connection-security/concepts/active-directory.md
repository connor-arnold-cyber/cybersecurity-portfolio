# Active Directory (AD)

## Overview

Active Directory (AD) is Microsoft's directory service for Windows domain environments. It provides centralized management of users, computers, groups, and other network resources while supporting authentication, authorization, and policy enforcement across an organization.

Rather than managing each computer individually, administrators manage resources from a central directory.

## Key Concepts

### Directory Service

Active Directory stores information about network objects, including:

- Users
- Computers
- Groups
- Printers
- Servers
- Organizational Units (OUs)

This information is organized in a hierarchical structure that makes resources easy to locate and manage.

### Domain

A domain is a collection of computers and users that share the same Active Directory database and security policies.

Users can authenticate once and access resources throughout the domain based on their permissions.

### Domain Controller (DC)

A Domain Controller is a server that hosts the Active Directory database.

Its responsibilities include:

- Authenticating users
- Authorizing access
- Storing directory information
- Enforcing Group Policy
- Replicating directory data with other Domain Controllers

### Organizational Units (OUs)

Organizational Units are containers used to organize objects within Active Directory.

Administrators commonly group objects by:

- Department
- Location
- Function
- Device type

OUs simplify management and allow different policies to be applied to different parts of the organization.

### Group Policy

Group Policy allows administrators to centrally configure Windows computers and user settings.

Common uses include:

- Password policies
- Security settings
- Software deployment
- Desktop configuration
- Login scripts
- Windows Update settings

Policies automatically apply to users and computers within their assigned scope.

### Authentication

Active Directory commonly uses **Kerberos** as its primary authentication protocol.

LDAP is used to query and manage directory information, while Kerberos verifies user identities.

## Active Directory Components

| Component | Purpose |
|----------|---------|
| Domain | Logical boundary for users and resources |
| Domain Controller | Stores the directory and authenticates users |
| Organizational Unit (OU) | Organizes objects for administration |
| Group Policy | Centrally manages system and user settings |
| Kerberos | Authenticates users |
| LDAP | Accesses directory information |

## Why It Matters

Active Directory is the foundation of identity and access management in many enterprise Windows environments. Security professionals regularly interact with Active Directory during system administration, incident response, penetration testing, and threat hunting because it controls authentication and authorization across the network.

## Common Uses

- Enterprise identity management
- Windows domain administration
- Centralized authentication
- Group Policy management
- User and computer management
- Access control
- Network administration

## Best Practices

- Apply the Principle of Least Privilege.
- Protect Domain Controllers because they are critical infrastructure.
- Regularly review privileged group memberships.
- Monitor authentication and directory service logs.
- Keep Active Directory and Domain Controllers fully patched.
- Use Multi-Factor Authentication for privileged accounts whenever possible.
