# Diffie-Hellman

## Overview

Diffie-Hellman is a key exchange algorithm that allows two parties to securely establish a shared secret key over an insecure network. The shared key is then used for symmetric encryption.

Diffie-Hellman does not encrypt data itself.

## Key Concepts

- Key Exchange
- Shared Secret
- Public Values
- Session Key
- Perfect Forward Secrecy

## Why It Matters

Diffie-Hellman solves one of the biggest problems in cryptography: how to securely create a shared secret without ever transmitting the secret itself. This makes secure communication possible over untrusted networks like the Internet.

## Common Uses

- TLS
- HTTPS
- VPNs
- SSH
- Secure Messaging

## Best Practices

- Generate a new shared secret for each session.
- Use modern implementations such as Elliptic Curve Diffie-Hellman (ECDH).
- Combine Diffie-Hellman with symmetric encryption for data transmission.
- Protect long-term private keys.

## Related Labs & Projects

- Coming soon.
