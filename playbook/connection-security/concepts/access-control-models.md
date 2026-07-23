# Access Control Models

## Overview

Access control models define the rules used to determine who can access resources and what actions they are allowed to perform. Organizations choose an access control model based on their security requirements, operational needs, and regulatory obligations.

The four primary access control models are:

- Discretionary Access Control (DAC)
- Mandatory Access Control (MAC)
- Role-Based Access Control (RBAC)
- Attribute-Based Access Control (ABAC)

## Key Concepts

### Discretionary Access Control (DAC)

In DAC, the owner of a resource decides who can access it.

For example, a user who creates a file can grant or revoke permissions for other users.

**Advantages**

- Flexible
- Easy to manage

**Disadvantages**

- Permissions can be shared unintentionally
- Less secure in highly sensitive environments

### Mandatory Access Control (MAC)

In MAC, access decisions are enforced by a central authority based on security classifications and labels.

Users cannot change permissions on their own.

MAC is commonly used in government and military environments.

**Advantages**

- Very secure
- Centralized control

**Disadvantages**

- Complex to administer
- Less flexible

### Role-Based Access Control (RBAC)

RBAC assigns permissions based on a user's role within an organization.

Instead of assigning permissions individually, users inherit permissions from their assigned role.

Examples:

- Administrator
- Manager
- Help Desk Technician
- Standard User

RBAC simplifies administration and is widely used in enterprise environments.

### Attribute-Based Access Control (ABAC)

ABAC makes access decisions based on attributes rather than fixed roles.

Examples of attributes include:

- User department
- Job title
- Device type
- Time of day
- Geographic location
- Security clearance

ABAC provides highly granular and dynamic access control.

## Comparison

| Model | Access Based On | Common Use |
|--------|-----------------|------------|
| DAC | Resource owner | Personal computers, file sharing |
| MAC | Security labels | Government, military |
| RBAC | Organizational role | Enterprise environments |
| ABAC | Attributes and policies | Cloud services, zero trust environments |

## Why It Matters

Access control models determine how organizations protect sensitive resources. Choosing the appropriate model helps balance security, usability, and administrative overhead while enforcing the Principle of Least Privilege.

## Common Uses

- Operating systems
- Enterprise networks
- Cloud platforms
- Databases
- File systems
- Identity and Access Management (IAM)

## Best Practices

- Apply the Principle of Least Privilege.
- Grant only the permissions necessary for each role or policy.
- Review permissions regularly.
- Prefer RBAC for most enterprise environments.
- Use ABAC when dynamic, context-aware access decisions are required.
