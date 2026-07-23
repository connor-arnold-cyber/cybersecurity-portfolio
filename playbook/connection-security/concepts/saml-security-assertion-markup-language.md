# Security Assertion Markup Language (SAML)

## Overview

Security Assertion Markup Language (SAML) is an XML-based standard used to exchange authentication and authorization information between an Identity Provider (IdP) and a Service Provider (SP).

SAML is commonly used to implement Single Sign-On (SSO), allowing users to authenticate once and access multiple applications without repeatedly entering their credentials.

## Key Concepts

### Identity Provider (IdP)

The Identity Provider authenticates the user.

After successful authentication, it creates and signs a SAML assertion that confirms the user's identity.

Examples include Microsoft Entra ID, Okta, and Ping Identity.

### Service Provider (SP)

The Service Provider is the application the user wants to access.

Instead of authenticating the user directly, it validates the SAML assertion received from the Identity Provider before granting access.

### SAML Assertion

A SAML assertion is an XML document containing information about the authenticated user.

A SAML assertion may include:

- User identity
- Authentication status
- Authorization information
- Token expiration
- Additional user attributes

The assertion is digitally signed to ensure its authenticity and integrity.

### Trust Relationship

SAML requires an established trust relationship between the Identity Provider and the Service Provider.

The Service Provider trusts assertions signed by the configured Identity Provider.

### Single Sign-On

SAML enables Single Sign-On by allowing authentication to occur once.

After authenticating with the Identity Provider, users can access multiple trusted applications without logging in again.

## SAML Authentication Flow

A simplified SAML authentication process is:

1. The user attempts to access an application.
2. The application redirects the user to the Identity Provider.
3. The user authenticates with the Identity Provider.
4. The Identity Provider creates and digitally signs a SAML assertion.
5. The user's browser sends the assertion to the Service Provider.
6. The Service Provider validates the assertion.
7. If valid, access is granted.

## SAML vs. OpenID Connect

| SAML | OpenID Connect (OIDC) |
|------|------------------------|
| XML-based | JSON-based |
| Common in enterprise environments | Common in web and mobile applications |
| Primarily browser-based | Designed for modern APIs and applications |
| Often used for enterprise SSO | Often used for cloud and consumer authentication |

## Why It Matters

SAML is one of the most widely deployed enterprise authentication standards. It enables organizations to centralize authentication, improve user experience, and reduce password management by supporting secure Single Sign-On across many applications.

## Common Uses

- Enterprise Single Sign-On (SSO)
- Microsoft 365
- Salesforce
- Workday
- Educational institutions
- Government organizations
- Cloud applications

## Best Practices

- Exchange SAML assertions only over HTTPS.
- Verify digital signatures before trusting assertions.
- Configure trust relationships carefully.
- Limit assertion lifetime to reduce risk.
- Protect Identity Provider accounts with Multi-Factor Authentication (MFA).
