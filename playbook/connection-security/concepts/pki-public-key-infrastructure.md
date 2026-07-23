# Public Key Infrastructure (PKI)

## Overview

Public Key Infrastructure (PKI) is the framework of technologies, policies, hardware, software, and trusted organizations that manages digital certificates and public key encryption.

PKI establishes trust between systems by issuing, validating, renewing, and revoking digital certificates used for secure communications.

## Key Concepts

### Public and Private Keys

PKI uses asymmetric encryption, where each entity has two mathematically related keys:

- **Public key** – Shared with others and used to encrypt data or verify digital signatures.
- **Private key** – Kept secret and used to decrypt data or create digital signatures.

Only the matching private key can decrypt data encrypted with the corresponding public key.

### Certificate Authority (CA)

A Certificate Authority (CA) is a trusted organization responsible for issuing and digitally signing certificates.

Clients trust certificates because they trust the CA that issued them.

Examples include commercial CAs as well as internal enterprise CAs.

### Registration Authority (RA)

A Registration Authority (RA) verifies the identity of entities requesting certificates.

Once identity is confirmed, the RA authorizes the CA to issue the certificate.

Not every PKI deployment includes a separate RA.

### Digital Certificates

PKI manages the complete lifecycle of digital certificates, including:

- Issuance
- Renewal
- Validation
- Revocation
- Expiration

Certificates bind an identity to a public key.

### Certificate Revocation

If a certificate is compromised or should no longer be trusted, it can be revoked before its expiration date.

Clients may check certificate status using mechanisms such as:

- Certificate Revocation Lists (CRLs)
- Online Certificate Status Protocol (OCSP)

## Why It Matters

PKI provides the trust required for secure communications across the Internet and private networks. It enables systems to authenticate one another, exchange encrypted information, and verify digital signatures without sharing private keys.

Without PKI, technologies such as HTTPS, VPNs, secure email, and code signing would not function securely.

## Common Uses

- HTTPS websites
- TLS authentication
- VPN authentication
- Secure email
- Digital signatures
- Code signing
- Device authentication
- Enterprise certificate management

## Best Practices

- Protect private keys with strong access controls.
- Use trusted Certificate Authorities.
- Monitor certificate expiration dates.
- Revoke compromised certificates immediately.
- Regularly audit PKI infrastructure and certificate inventories.
