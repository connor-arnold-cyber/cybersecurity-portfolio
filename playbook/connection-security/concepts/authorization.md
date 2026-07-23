# Authorization

## Overview

Authorization is the process of determining what an authenticated user, device, or application is allowed to access or do within a system.

Authorization answers the question:

> "What are you allowed to do?"

It occurs **after authentication** and enforces access control by granting or denying permissions based on predefined policies.

## Key Concepts

### Permissions

Authorization determines which resources a user can:

- View
- Create
- Modify
- Delete
- Execute

Permissions are assigned based on organizational policies and business requirements.

### Access Control

Authorization is implemented through access control mechanisms that define who can access specific resources.

Common access control models include:

- Role-Based Access Control (RBAC)
- Attribute-Based Access Control (ABAC)
- Discretionary Access Control (DAC)
- Mandatory Access Control (MAC)

### Principle of Least Privilege

Users should receive only the permissions necessary to perform their required tasks.

Limiting permissions reduces the impact of compromised accounts and accidental misuse.

### Roles

Many organizations assign permissions through roles rather than individual user accounts.

For example:

- Administrator
- Manager
- Standard User
- Guest

Changing a user's role automatically updates their permissions.

### Access Decisions

After successful authentication, the system evaluates authorization rules to determine whether a requested action should be allowed.

Possible outcomes include:

- Access granted
- Access denied
- Limited access

## Authentication vs. Authorization

| Authentication | Authorization |
|---------------|---------------|
| Verifies identity | Determines permissions |
| Answers "Who are you?" | Answers "What are you allowed to do?" |
| Happens first | Happens after authentication |
| Validates credentials | Applies access policies |

## Why It Matters

Authorization protects sensitive resources by ensuring users can access only what they are permitted to use. Even if an attacker successfully authenticates, effective authorization limits what they can view or modify.

Strong authorization is a critical layer of defense against privilege abuse and unauthorized access.

## Common Uses

- File permissions
- Operating systems
- Cloud platforms
- Enterprise applications
- Databases
- APIs
- Network devices

## Best Practices

- Follow the Principle of Least Privilege.
- Assign permissions using roles whenever possible.
- Regularly review and remove unnecessary permissions.
- Separate administrative and standard user accounts.
- Audit authorization policies and access logs regularly.
