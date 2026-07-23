# Hashing

## Overview

Hashing is the process of converting data of any size into a fixed-length value called a **hash** or **message digest**. Unlike encryption, hashing is a **one-way function**, meaning the original data cannot be recovered from the hash.

Hashing is primarily used to verify data integrity, securely store passwords, and support digital signatures.

## Key Concepts

### One-Way Function

A hash function is designed to be irreversible.

Given the same input, it always produces the same output, but the original input cannot feasibly be determined from the hash alone.

### Fixed-Length Output

Regardless of the size of the input, the resulting hash is always the same length for a given hashing algorithm.

For example, both a one-word message and a large file produce hashes of identical length when using the same algorithm.

### Deterministic

Hash functions are deterministic.

This means identical input always produces the exact same hash value.

If the input changes by even one character, the resulting hash changes dramatically.

### Data Integrity

Hashes allow systems to verify that data has not been altered.

A file's hash can be calculated before and after transmission. If both hashes match, the file has not changed.

### Password Storage

Modern systems store password hashes instead of plaintext passwords.

When a user logs in:

1. The entered password is hashed.
2. The new hash is compared to the stored hash.
3. If they match, authentication succeeds.

The original password is never stored.

### Common Algorithms

Common hashing algorithms include:

- SHA-256
- SHA-384
- SHA-512
- SHA-3
- BLAKE2

Older algorithms such as **MD5** and **SHA-1** are considered cryptographically broken and should not be used for security purposes.

## Hashing vs. Encryption

| Hashing | Encryption |
|---------|------------|
| One-way | Two-way |
| Cannot be reversed | Can be decrypted with the proper key |
| Used for integrity and verification | Used for confidentiality |
| No decryption key | Requires encryption and decryption keys |

## Why It Matters

Hashing helps detect unauthorized changes to data and protects sensitive information such as passwords. It is one of the most widely used security technologies and forms the foundation of digital signatures, certificate validation, software verification, and many authentication systems.

## Common Uses

- Password storage
- File integrity verification
- Digital signatures
- Software verification
- Malware analysis
- Certificate validation
- Blockchain technologies

## Best Practices

- Use modern algorithms such as SHA-256 or SHA-3.
- Never use MD5 or SHA-1 for security-sensitive applications.
- Store passwords using a dedicated password hashing algorithm (such as bcrypt, Argon2, or PBKDF2) rather than a general-purpose hash function.
- Verify downloaded files using published hashes whenever available.
- Protect hash databases from unauthorized access.
