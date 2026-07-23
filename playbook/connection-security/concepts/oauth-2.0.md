# OAuth 2.0

## Overview

OAuth 2.0 is an authorization framework that allows a user to grant an application limited access to their resources without sharing their password.

Instead of giving the application their login credentials, the user authorizes access through a trusted Identity Provider, which issues an access token with specific permissions.

OAuth 2.0 is designed for **authorization**, not authentication.

## Key Concepts

### Authorization

OAuth 2.0 answers the question:

> "What is this application allowed to access?"

It does **not** verify the user's identity.

Authentication is commonly provided by OpenID Connect (OIDC), which extends OAuth 2.0.

### Access Token

After the user grants permission, the authorization server issues an **access token**.

The application presents this token when requesting access to protected resources.

The token represents the permissions granted by the user.

### Scope

A scope defines what an application is allowed to do.

Examples include:

- Read email
- View profile information
- Access cloud storage
- Read contacts
- Upload files

Applications should request only the permissions they actually need.

### Authorization Server

The Authorization Server is responsible for:

- Authenticating the user
- Obtaining user consent
- Issuing access tokens
- Managing token expiration

Examples include Microsoft Entra ID, Google Identity, and Okta.

### Resource Server

The Resource Server stores the protected data.

Before granting access, it validates the access token to ensure the request is authorized.

## OAuth 2.0 Flow

A simplified OAuth 2.0 process is:

1. The application requests access to a user's resources.
2. The user authenticates with the Authorization Server.
3. The user approves the requested permissions.
4. The Authorization Server issues an access token.
5. The application presents the token to the Resource Server.
6. If the token is valid, access is granted.

## OAuth 2.0 vs. OpenID Connect

| OAuth 2.0 | OpenID Connect (OIDC) |
|-----------|-----------------------|
| Authorization framework | Authentication layer built on OAuth 2.0 |
| Grants resource access | Verifies user identity |
| Issues access tokens | Issues ID tokens in addition to access tokens |
| Answers "What can this app access?" | Answers "Who is the user?" |

## Why It Matters

OAuth 2.0 allows users to safely authorize third-party applications without exposing their passwords. It is widely used by cloud services, APIs, mobile applications, and web applications to provide secure delegated access.

## Common Uses

- "Sign in with Google"
- "Continue with Microsoft"
- Cloud storage integrations
- Social media integrations
- Mobile applications
- REST APIs
- Third-party web applications

## Best Practices

- Request only the minimum scopes required.
- Protect access tokens from unauthorized disclosure.
- Use HTTPS for all OAuth communications.
- Validate tokens before granting access.
- Use OpenID Connect when user authentication is also required.
