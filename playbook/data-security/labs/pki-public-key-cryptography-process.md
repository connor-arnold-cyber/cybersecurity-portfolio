# Lab: Cryptographic Solutions

## Overview

This lab demonstrates how public key cryptography is used to protect the authenticity, integrity, and trustworthiness of digital information. Using OpenSSL, RSA key pairs are generated, digital signatures are created and verified, and a Certificate Signing Request (CSR) is signed by a Certificate Authority (CA) to produce a trusted digital certificate.

## Lab Summary

This lab follows the lifecycle of asymmetric cryptography:

1. Generate an RSA public/private key pair.
2. Use the private key to digitally sign a file.
3. Verify the signature using the corresponding public key.
4. Create a Certificate Signing Request (CSR).
5. Have a Certificate Authority sign the CSR.
6. Receive a trusted digital certificate.

## Key Takeaways

- RSA key pairs enable secure public key cryptography.
- Digital signatures provide authenticity and integrity.
- SHA-256 detects file modifications.
- A CSR requests a trusted certificate without exposing the private key.
- Certificate Authorities establish trust by signing certificates.
- PKI combines these components into a trusted cryptographic ecosystem.

## Workflow

### Generate an RSA Key Pair

Created an RSA private key and derived the matching public key.

**Purpose**

- Establish an asymmetric key pair.
- Keep the private key secret.
- Share the public key for verification and encryption.

### Create a Digital Signature

Generated a SHA-256 hash of a file and encrypted the hash with the private key to create a digital signature.

**Purpose**

- Prove the sender's identity.
- Protect the integrity of the file.
- Detect any modifications.

### Verify the Digital Signature

Verified the signature using the public key.

**Result**

- Original file → Verification succeeded.
- Modified file → Verification failed.

This demonstrates that any change to the file changes its hash, causing signature verification to fail.

### Create a Certificate Signing Request (CSR)

Generated a CSR containing:

- Public key
- Organization information
- Common Name (CN)

The CSR was submitted to a Certificate Authority.

**Purpose**

Request a trusted certificate without exposing the private key.

### Sign the CSR with a Certificate Authority

The CA verified the request and signed it using its own private key, producing a digital certificate.

**Purpose**

Establish trust between the public key and the identity contained in the certificate.

### Verify the Certificate

Confirmed that the issued certificate could be validated against the CA's certificate.

This demonstrates the trust model used by HTTPS, VPNs, code signing, email security, and many enterprise authentication systems.

## Notes

### Digital Signature Process

```text
File
 │
 ▼
SHA-256 Hash
 │
 ▼
Encrypted with Private Key
 │
 ▼
Digital Signature

Receiver

File ──► SHA-256 Hash
            │
            ▼
Decrypt Signature with Public Key
            │
            ▼
Hashes Match?
      │
      ├── Yes → Authentic & Unmodified
      └── No  → Modified or Invalid
```

### Certificate Issuance Process

```text
Client
 │
 │ Generates RSA Key Pair
 ▼
Private Key      Public Key
      │
      ▼
Generate CSR
      │
      ▼
Certificate Authority
      │
Signs CSR with CA Private Key
      │
      ▼
Digital Certificate
      │
      ▼
Trusted by systems that trust the CA
```

## Quick Reference

| Item | Purpose |
|------|---------|
| OpenSSL | Cryptographic toolkit used throughout the lab |
| RSA | Generates the public/private key pair |
| Private Key | Creates digital signatures and must remain secret |
| Public Key | Verifies signatures and is shared with others |
| Command: dgst | Creates or verifies a cryptographic hash |
| SHA-256 | Hashing algorithm used to verify integrity |
| Digital Signature | Proves authenticity and integrity |
| CSR | Requests a signed certificate from a CA |
| CA | Verifies identity and signs certificates |
| Digital Certificate | Binds an identity to a public key |
| Signature Verification Failure | Indicates the file or signature has been altered |

## Related Playbook Pages

- [RSA](../concepts/rsa.md)
- [Asymmetric Encryption](../concepts/asymmetric-encryption.md)
- [Public & Private Key Encryption](../../connection-security/concepts/public-&-private-key-encryption.md)
- [Hashing](../concepts/hashing.md)
- [SHA-256](../concepts/sha-256.md)
- [Digital Signatures](../concepts/digital-signatures.md)
- [Certificate Signing Requests (CSRs)](../../connection-security/concepts/csr-certificate-signing-requests.md)
- [Certificate Authority (CA)](../../connection-security/concepts/certificate-authority.md)
- [Digital Certificates](../../connection-security/concepts/digital-certificates.md)
- [Public Key Infrastructure (PKI)](../../connection-security/concepts/pki-public-key-infrastructure.md)
