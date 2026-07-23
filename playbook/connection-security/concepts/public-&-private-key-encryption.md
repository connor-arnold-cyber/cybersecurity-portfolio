# Public and Private Key Encryption

## Overview

Public and private key encryption, also called **asymmetric encryption**, is a cryptographic system that uses two mathematically related keys: a public key that can be shared with anyone and a private key that is kept secret.

Unlike symmetric encryption, the two keys perform different functions. Data encrypted with one key can only be decrypted with the other.

Asymmetric encryption is widely used for secure communication, authentication, digital signatures, and key exchange.

## Key Concepts

### Public Key

The public key is intended to be shared freely.

It can be used to:

- Encrypt data
- Verify digital signatures

Because it cannot be used to derive the private key, it is safe to distribute publicly.

### Private Key

The private key is kept secret by its owner.

It is used to:

- Decrypt data encrypted with the public key
- Create digital signatures

If a private key is compromised, the security of the entire key pair is compromised.

### Encryption

When confidentiality is required:

1. The sender encrypts data using the recipient's public key.
2. The recipient decrypts the data using their private key.

Only the intended recipient possesses the private key needed to read the message.

### Digital Signatures

Asymmetric encryption can also prove authenticity.

A sender signs data using their private key.

Recipients verify the signature using the sender's public key.

This confirms:

- The sender's identity
- That the data has not been modified

### Key Exchange

Because asymmetric encryption is computationally expensive, it is commonly used to securely exchange symmetric session keys.

Protocols such as TLS use asymmetric encryption during the handshake and then switch to faster symmetric encryption for the remainder of the session.

## Public vs. Private Keys

| Public Key | Private Key |
|------------|-------------|
| Shared freely | Kept secret |
| Encrypts data | Decrypts data |
| Verifies digital signatures | Creates digital signatures |
| Distributed to others | Never shared |

## Why It Matters

Public and private key encryption allows systems to communicate securely without first sharing a secret key. It provides confidentiality, authentication, integrity, and non-repudiation, making it a foundational technology for modern cybersecurity.

## Common Uses

- TLS/HTTPS
- Public Key Infrastructure (PKI)
- Digital certificates
- Digital signatures
- Secure email
- VPN authentication
- SSH authentication

## Best Practices

- Never share private keys.
- Protect private keys with strong access controls.
- Rotate compromised keys immediately.
- Use sufficiently strong key sizes.
- Use asymmetric encryption for authentication and key exchange, then switch to symmetric encryption for bulk data encryption.
