# JSON Web Token (JWT)

## Overview

A JSON Web Token (JWT) is a compact, digitally signed token used to securely transmit information between two parties. JWTs are commonly used by OAuth 2.0 and OpenID Connect (OIDC) to represent authenticated users and authorized sessions.

Because JWTs are digitally signed, recipients can verify that the information has not been altered.

## Key Concepts

### Token-Based Authentication

Instead of repeatedly sending a username and password, a user authenticates once and receives a JWT.

The application presents the JWT with future requests to prove the user's identity or permissions.

### JWT Structure

A JWT consists of three Base64URL-encoded parts separated by periods:

```text
Header.Payload.Signature
```

- **Header** – Specifies the token type and signing algorithm.
- **Payload** – Contains claims about the user or session.
- **Signature** – Protects the token from unauthorized modification.

### Claims

Claims are pieces of information stored inside the payload.

Common claims include:

- User ID
- Username
- Email address
- Roles
- Token issuer
- Expiration time

Applications use these claims to make authentication and authorization decisions.

### Digital Signature

The signature is created using a secret key or a private key.

When a server receives a JWT, it verifies the signature before trusting the token's contents.

If the token has been modified, signature verification fails.

### Expiration

JWTs include an expiration time to limit how long they remain valid.

Once expired, users typically need to authenticate again or use a refresh token to obtain a new JWT.

## JWT vs. Sessions

| JWT | Traditional Session |
|-----|----------------------|
| Stored by the client | Session data stored on the server |
| Sent with each request | Session ID sent with each request |
| Digitally signed | Server validates session ID |
| Scales well for distributed systems | Requires shared session storage in many environments |

## Why It Matters

JWTs enable secure, stateless authentication for modern web applications and APIs. They reduce the need for server-side session storage while allowing applications to verify user identity and permissions using digitally signed tokens.

JWTs are widely used in cloud services, REST APIs, mobile applications, and Single Sign-On solutions.

## Common Uses

- OpenID Connect (OIDC)
- OAuth 2.0
- REST APIs
- Single Sign-On (SSO)
- Web applications
- Mobile applications
- Cloud services

## Best Practices

- Always transmit JWTs over HTTPS.
- Verify the token's digital signature before trusting its contents.
- Check token expiration before granting access.
- Store tokens securely to prevent theft.
- Never store sensitive information directly inside a JWT payload unless it is appropriately protected.
