# Hashing

## Overview

Hashing is the process of converting data into a fixed-length hash value using a one-way mathematical function. The original data cannot be recreated from the hash.

Hashing is primarily used to verify data integrity.

## Key Concepts

- Hash Function
- Hash Value
- One-Way Function
- SHA-256
- MD5
- Collision

## Why It Matters

Hashing allows systems to detect unauthorized changes to data. Even a one-character change produces a completely different hash value.

## Common Uses

- Password Storage
- File Integrity Monitoring
- Digital Signatures
- Software Verification

## Best Practices

- Use strong hashing algorithms such as SHA-256.
- Avoid deprecated algorithms like MD5 for security.
- Do not use hashing as a replacement for encryption.

## Related Concepts

## Related Concepts

- [Encryption](encryption.md) — Protects confidentiality by converting plaintext into ciphertext.
- [Digital Signatures](digital-signatures.md) — Use hashing to verify authenticity, integrity, and non-repudiation.
- [File Integrity Monitoring](../system-security/file-integrity-monitoring.md) — Uses hashes to detect unauthorized changes to files.
- Public Key Infrastructure (PKI) *(Coming Soon)*
- Certificates *(Coming Soon)*
- SHA-256 *(Coming Soon)*

## Related Labs & Projects

- Coming soon.
