# OpenID Connect (OIDC)

## Overview

OpenID Connect (OIDC) is an authentication protocol built on top of OAuth 2.0. It allows applications to verify a user's identity while also supporting secure authorization.

While OAuth 2.0 answers the question, **"What is this application allowed to access?"**, OpenID Connect answers, **"Who is the user?"**

## Key Concepts

### Authentication

OpenID Connect provides user authentication.

After a user successfully signs in, the Identity Provider confirms the user's identity to the application.

### Identity Provider (IdP)

The Identity Provider authenticates the user and issues tokens.

Its responsibilities include:

- Verifying user credentials
- Managing user identities
- Issuing ID Tokens
- Issuing Access Tokens

Examples include Microsoft Entra ID, Google Identity, Okta, and Auth0.

### ID Token

An **ID Token** is the primary feature that distinguishes OpenID Connect from OAuth 2.0.

The ID Token contains information about the authenticated user, such as:

- User identifier
- Authentication time
- Token expiration
- Identity claims

Applications use the ID Token to verify the user's identity.

### Access Token

OpenID Connect also supports OAuth 2.0 Access Tokens.

These tokens allow applications to access protected resources after authentication.

The ID Token proves **who the user is**, while the Access Token determines **what resources the application may access**.

### Claims

Claims are pieces of information about the authenticated user.

Examples include:

- Name
- Email address
- Username
- User ID
- Preferred language

Applications can use claims to personalize the user experience.

## OpenID Connect vs. OAuth 2.0

| OpenID Connect | OAuth 2.0 |
|----------------|-----------|
| Authentication protocol | Authorization framework |
| Verifies user identity | Grants resource access |
| Issues ID Tokens | Issues Access Tokens |
| Answers "Who is the user?" | Answers "What can the application access?" |

## Why It Matters

OpenID Connect provides a standardized way for applications to authenticate users while leveraging the authorization capabilities of OAuth 2.0. It is widely used in cloud services, mobile applications, enterprise environments, and Single Sign-On (SSO) solutions.

## Common Uses

- Single Sign-On (SSO)
- Cloud applications
- Mobile applications
- Enterprise identity platforms
- Customer login portals
- "Sign in with Google"
- "Sign in with Microsoft"

## Best Practices

- Always use HTTPS for OpenID Connect communications.
- Validate ID Tokens before trusting user identity.
- Protect authentication tokens from unauthorized access.
- Request only the user information needed by the application.
- Combine OpenID Connect with Multi-Factor Authentication (MFA) whenever possible.
