# Perfect Forward Secrecy (PFS)

## Overview

Perfect Forward Secrecy (PFS) is a security feature that generates a unique session key for every communication session. This ensures that if a long-term private key is ever compromised, previously encrypted communications remain secure.

PFS is commonly achieved using ephemeral Diffie-Hellman key exchange.

## Key Concepts

- Session Key
- Diffie-Hellman
- Ephemeral Keys
- Key Exchange
- TLS

## Why It Matters

Without Perfect Forward Secrecy, an attacker who later obtains a server's private key could potentially decrypt previously captured encrypted traffic. PFS prevents this by ensuring each session uses a temporary key that is discarded after the session ends.

## Common Uses

- HTTPS
- TLS
- VPNs
- Secure Messaging
- SSH

## Best Practices

- Enable Perfect Forward Secrecy whenever supported.
- Use ephemeral Diffie-Hellman (DHE or ECDHE) for key exchange.
- Generate a new session key for every connection.
- Keep cryptographic software up to date.

## Related Labs & Projects

- Coming soon.
