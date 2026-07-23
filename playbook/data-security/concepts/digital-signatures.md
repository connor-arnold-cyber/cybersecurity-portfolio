# Digital Signatures

## Overview

A digital signature is a cryptographic mechanism used to verify the authenticity, integrity, and origin of digital data. It allows recipients to confirm that data was created by the claimed sender and has not been altered since it was signed.

Digital signatures use asymmetric cryptography and are commonly used alongside Public Key Infrastructure (PKI).

## Key Concepts

### Authentication

A digital signature verifies the identity of the sender.

Because only the owner possesses the private key used to create the signature, a valid signature provides confidence that the data came from the expected source.

### Integrity

Digital signatures ensure that data has not been modified.

If even a single bit of the signed data changes, the signature verification will fail.

### Non-Repudiation

A properly implemented digital signature helps prevent the sender from denying they signed the data.

Since the signature was created using the sender's private key, it serves as evidence of authorship.

### How Digital Signatures Work

The signing process is generally:

1. The original data is hashed.
2. The hash is encrypted using the sender's private key.
3. The encrypted hash becomes the digital signature.
4. The signature is sent along with the original data.

To verify the signature:

1. The recipient hashes the received data.
2. The recipient decrypts the signature using the sender's public key.
3. The two hash values are compared.
4. If they match, the signature is valid.

### Relationship to Hashing

Digital signatures do not encrypt the entire file.

Instead, they sign a hash of the data, making the process much faster while still protecting integrity.

## Why It Matters

Digital signatures establish trust in electronic communications. They verify identities, detect tampering, and support secure transactions across the Internet.

Many modern security technologies rely on digital signatures to prevent unauthorized software, forged communications, and fraudulent certificates.

## Common Uses

- Code signing
- Software updates
- Digital certificates
- Secure email
- Electronic documents
- Financial transactions
- Public Key Infrastructure (PKI)

## Best Practices

- Protect private signing keys from unauthorized access.
- Use strong hashing algorithms with digital signatures.
- Verify signatures before trusting software or documents.
- Revoke compromised certificates immediately.
- Use trusted Certificate Authorities when validating digital signatures.
