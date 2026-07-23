# Hypertext Transfer Protocol Secure (HTTPS)

## Overview

Hypertext Transfer Protocol Secure (HTTPS) is the secure version of HTTP. It combines HTTP with Transport Layer Security (TLS) to encrypt communication between a client and a web server.

HTTPS protects the confidentiality and integrity of transmitted data while allowing users to verify the identity of the website they are connecting to.

## Key Concepts

### Encryption

HTTPS encrypts all data exchanged between the client and server using TLS.

This prevents attackers from reading sensitive information such as:

- Usernames and passwords
- Credit card numbers
- Personal information
- Session cookies

### Authentication

HTTPS uses digital certificates to verify that a website is genuine.

Certificates are issued by trusted Certificate Authorities (CAs) and help protect users from connecting to fraudulent websites.

### Data Integrity

HTTPS ensures that data cannot be modified while it is traveling across the network.

If transmitted data is altered, integrity checks detect the change and reject the modified data.

### HTTPS vs. HTTP

| HTTP | HTTPS |
|------|-------|
| Data is transmitted in plaintext | Data is encrypted using TLS |
| No identity verification | Server identity is verified with a digital certificate |
| Vulnerable to interception | Protects against eavesdropping and tampering |
| Default port 80 | Default port 443 |

### TLS

HTTPS relies on TLS to provide:

- Encryption
- Authentication
- Integrity

Without TLS, HTTPS would simply be standard HTTP.

## Why It Matters

HTTPS is the standard for secure web communication. It protects users from credential theft, data interception, and many forms of Man-in-the-Middle (MitM) attacks while providing confidence that they are communicating with the intended website.

## Common Uses

- Secure websites
- Online banking
- E-commerce
- Web applications
- REST APIs
- User authentication

## Best Practices

- Always use HTTPS instead of HTTP whenever possible.
- Use valid certificates issued by trusted Certificate Authorities.
- Keep TLS configurations up to date.
- Renew certificates before they expire.
- Verify certificate warnings instead of ignoring them.
