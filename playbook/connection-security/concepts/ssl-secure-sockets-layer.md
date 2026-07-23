# Secure Sockets Layer (SSL)

## Overview

Secure Sockets Layer (SSL) is a cryptographic protocol that was developed to secure communications over a network. It provided encryption, authentication, and data integrity for Internet communications.

SSL has been deprecated due to known security vulnerabilities and has been replaced by Transport Layer Security (TLS).

## Key Concepts

### Encryption

SSL encrypts data transmitted between a client and a server, preventing unauthorized parties from reading intercepted communications.

### Authentication

SSL uses digital certificates issued by trusted Certificate Authorities (CAs) to verify the identity of servers before secure communication begins.

### Integrity

SSL includes mechanisms to detect whether transmitted data has been altered while in transit.

If data is modified, the connection can be terminated to prevent the use of tampered information.

### SSL Handshake

Before encrypted communication begins, SSL performs a handshake to:

- Verify the server's identity
- Negotiate cryptographic algorithms
- Exchange encryption information
- Establish a secure session

Modern TLS handshakes perform the same function using stronger security mechanisms.

### Deprecation

Older versions of SSL contain weaknesses that make them vulnerable to several attacks.

Because of these vulnerabilities:

- SSL 2.0 is obsolete
- SSL 3.0 is obsolete
- Modern systems should use TLS instead

Although people often say "SSL certificate," nearly all modern secure websites actually use TLS.

## Why It Matters

Security professionals frequently encounter the term "SSL" even though modern secure communications rely on TLS. Understanding the relationship between SSL and TLS helps explain why older protocols should be disabled and why current systems use modern TLS versions.

## Common Uses

- Legacy secure web services
- Historical web security
- Legacy applications
- Understanding TLS evolution
- Certificate management terminology

## Best Practices

- Disable all SSL protocols on modern systems.
- Use current TLS versions for encrypted communications.
- Replace legacy applications that still require SSL.
- Keep cryptographic software updated.
- Understand that "SSL certificate" is common terminology even though the certificate is typically used with TLS.
