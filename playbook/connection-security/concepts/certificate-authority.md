# Certificate Authority (CA)

## Overview

A Certificate Authority (CA) is a trusted organization that verifies identities and issues digital certificates. By signing certificates with its own private key, a CA allows others to trust that a public key truly belongs to the person, device, or organization identified in the certificate.

Certificate Authorities are a core component of Public Key Infrastructure (PKI).

## Key Concepts

- [Digital Certificates](digital-certificates.md)
- Certificate Signing Request (CSR)
- Root CA
- Intermediate CA
- Trust Chain

## Why It Matters

Without a trusted Certificate Authority, anyone could create a public key and falsely claim to be someone else. CAs establish trust by verifying identities before issuing digital certificates.

## Common Uses

- HTTPS
- TLS
- Secure Email
- Code Signing
- VPN Authentication

## Best Practices

- Use trusted Certificate Authorities.
- Protect CA private keys.
- Verify identities before issuing certificates.
- Revoke compromised certificates promptly.
- Renew certificates before they expire.

## Related Labs & Projects

- Coming soon.
