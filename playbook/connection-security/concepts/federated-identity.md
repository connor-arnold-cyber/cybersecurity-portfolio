# Federated Identity

## Overview

Federated identity is an identity management approach that allows users to authenticate with one organization and use that identity to access resources owned by another trusted organization without creating a separate account.

Federated identity relies on trust relationships between organizations, allowing authentication to occur once while access is granted across multiple systems or domains.

## Key Concepts

### Trust Relationship

Federated identity is based on trust between organizations.

One organization agrees to trust another organization's authentication process instead of requiring users to create new credentials.

### Identity Provider (IdP)

The Identity Provider (IdP) authenticates the user.

After successful authentication, it issues a token or assertion that proves the user's identity.

### Service Provider (SP)

The Service Provider (SP) is the application or service the user wants to access.

Instead of authenticating the user directly, it trusts the Identity Provider's assertion and grants access based on that information.

### Authentication Tokens

After authentication, the Identity Provider issues a secure token that contains information about the user's identity.

The Service Provider validates the token before allowing access.

The user's password is not shared with the Service Provider.

### Federation Protocols

Common protocols used for federated identity include:

- SAML
- OAuth 2.0
- OpenID Connect (OIDC)

These standards allow organizations to securely exchange authentication information.

## Federated Identity vs. Single Sign-On

| Federated Identity | Single Sign-On (SSO) |
|--------------------|----------------------|
| Works across trusted organizations | Typically works within one organization |
| Shares identity between organizations | Shares authentication between applications |
| Requires trust relationships | Requires a central Identity Provider |
| Often uses SAML or OpenID Connect | Often uses SAML, OAuth, or OpenID Connect |

Federated identity and SSO are often used together, but they solve different problems.

## Why It Matters

Federated identity improves both security and usability by reducing the number of user accounts and passwords that must be managed. It also allows organizations to collaborate securely while maintaining control over their own user identities.

## Common Uses

- Microsoft 365
- Google Workspace
- University partnerships
- Government identity systems
- Business-to-business (B2B) applications
- Cloud services
- Customer identity platforms

## Best Practices

- Establish trust only with trusted organizations.
- Protect Identity Provider accounts with Multi-Factor Authentication (MFA).
- Use secure federation protocols such as SAML or OpenID Connect.
- Regularly review federation trust relationships.
- Monitor authentication logs for suspicious activity.
