# Symmetric Encryption

## Overview

Symmetric encryption is a cryptographic method that uses a **single shared key** to both encrypt and decrypt data. Both the sender and the recipient must possess the same secret key before secure communication can occur.

Because it is significantly faster than asymmetric encryption, symmetric encryption is the primary method used to protect large amounts of data.

## Key Concepts

### Shared Secret Key

Symmetric encryption relies on one secret key.

The same key is used to:

- Encrypt plaintext into ciphertext
- Decrypt ciphertext back into plaintext

Anyone who obtains the key can read the encrypted data.

### Speed

Symmetric encryption requires far less computational power than asymmetric encryption.

For this reason, it is commonly used to encrypt:

- Files
- Databases
- Disk drives
- Network sessions
- VPN traffic

### Key Distribution

The biggest challenge of symmetric encryption is securely sharing the secret key.

If an attacker intercepts the key during transmission, they can decrypt all protected communications.

Modern protocols such as TLS solve this by using asymmetric encryption to exchange the symmetric session key.

### Session Keys

Many secure communication protocols generate temporary symmetric keys called **session keys**.

A session key is used only for the duration of a single connection before being discarded.

This limits the impact if a session key is ever compromised.

### Common Algorithms

Common symmetric encryption algorithms include:

- AES (Advanced Encryption Standard)
- ChaCha20
- 3DES (legacy)
- DES (obsolete)

AES is the modern standard used by governments, businesses, and security products worldwide.

## Symmetric vs. Asymmetric Encryption

| Symmetric | Asymmetric |
|-----------|------------|
| One shared key | Public and private key pair |
| Very fast | Slower |
| Best for large amounts of data | Best for authentication and key exchange |
| Key must be shared securely | Public key can be distributed freely |

## Why It Matters

Nearly all encrypted Internet traffic ultimately relies on symmetric encryption because of its speed and efficiency. Technologies such as TLS, VPNs, Wi-Fi encryption, and full-disk encryption all use symmetric algorithms to protect data after a secure key exchange has taken place.

## Common Uses

- Full-disk encryption
- File encryption
- VPN tunnels
- TLS session encryption
- Wi-Fi encryption
- Database encryption
- Backup encryption

## Best Practices

- Use modern algorithms such as AES.
- Protect symmetric keys from unauthorized access.
- Rotate keys when appropriate.
- Use unique session keys for network communications.
- Never transmit secret keys in plaintext.
