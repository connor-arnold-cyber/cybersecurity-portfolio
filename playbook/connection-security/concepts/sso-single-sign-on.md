# Single Sign-On (SSO)

## Overview

Single Sign-On (SSO) is an authentication method that allows a user to log in once and gain access to multiple applications or services without needing to authenticate separately to each one.

Instead of maintaining separate credentials for every application, users authenticate with a central identity provider that verifies their identity on behalf of connected services.

## Key Concepts

### Centralized Authentication

SSO relies on a central authentication service called an **Identity Provider (IdP)**.

The Identity Provider verifies the user's credentials and informs connected applications that the user has been successfully authenticated.

### Identity Provider (IdP)

The Identity Provider is responsible for:

- Authenticating users
- Managing identities
- Issuing authentication tokens
- Establishing trust with connected applications

Examples include Microsoft Entra ID (formerly Azure AD), Okta, and Google Identity.

### Service Provider (SP)

A Service Provider is an application or website that trusts the Identity Provider to authenticate users.

Instead of requesting a username and password directly, the Service Provider accepts the authentication token issued by the IdP.

### Authentication Tokens

After successful authentication, the Identity Provider issues a secure token.

The Service Provider validates the token before granting access.

Because the token represents a successful login, the user does not need to enter credentials again for each connected application.

### Common Protocols

SSO commonly uses protocols such as:

- SAML
- OAuth 2.0
- OpenID Connect (OIDC)

These protocols allow applications from different vendors to trust the same Identity Provider.

## Benefits

Single Sign-On provides several advantages:

- Fewer passwords for users to remember
- Faster access to applications
- Improved user experience
- Centralized authentication management
- Easier enforcement of security policies such as MFA

## Why It Matters

SSO simplifies authentication while improving security. Organizations can enforce consistent authentication policies, reduce password reuse, and centralize account management across many applications.

Although SSO reduces the number of logins, it also makes protecting the central Identity Provider extremely important because many systems depend on it.

## Common Uses

- Enterprise environments
- Cloud applications
- Microsoft 365
- Google Workspace
- Corporate portals
- Educational institutions
- Customer identity platforms

## Best Practices

- Require Multi-Factor Authentication (MFA) for SSO accounts.
- Protect the Identity Provider with strong security controls.
- Use secure protocols such as SAML or OpenID Connect.
- Regularly review user access and connected applications.
- Monitor authentication logs for suspicious activity.
