# Certificate Authority (CA)

## Overview

A Certificate Authority (CA) is a trusted organization that issues, validates, renews, and revokes digital certificates. By digitally signing certificates, a CA allows users and systems to verify the identity of websites, servers, devices, and individuals.

Certificate Authorities are a core component of Public Key Infrastructure (PKI).

## Key Concepts

### Trust

A CA acts as a trusted third party.

Operating systems and web browsers maintain a list of trusted root CAs. When a certificate is signed by one of these trusted authorities (or one of its intermediates), clients can verify the certificate's authenticity.

### Certificate Issuance

Before issuing a certificate, a CA verifies the identity of the requesting entity.

Once verified, the CA:

1. Confirms the requester's identity.
2. Creates a digital certificate.
3. Digitally signs the certificate.
4. Issues the certificate to the requester.

### Digital Signature

Every certificate issued by a CA contains the CA's digital signature.

When a client receives the certificate, it verifies this signature using the CA's public key. If verification succeeds, the certificate is considered trustworthy.

### Root and Intermediate CAs

Most PKI deployments use a hierarchy of Certificate Authorities.

- **Root CA** – The highest level of trust. Root certificates are stored in operating systems and browsers.
- **Intermediate CA** – Issues certificates on behalf of the Root CA, reducing the need to expose the root private key.

This layered design improves security and simplifies certificate management.

### Certificate Revocation

If a certificate is compromised, expires prematurely, or should no longer be trusted, the CA can revoke it.

Clients can check certificate status using:

- Certificate Revocation Lists (CRLs)
- Online Certificate Status Protocol (OCSP)

## Why It Matters

Certificate Authorities establish trust on the Internet. Without trusted CAs, users would have no reliable way to determine whether they are communicating with legitimate websites or malicious impersonators.

Nearly all secure web communications rely on trusted Certificate Authorities.

## Common Uses

- HTTPS websites
- TLS certificates
- VPN authentication
- Secure email
- Code signing
- Device authentication
- Enterprise PKI

## Best Practices

- Obtain certificates only from trusted Certificate Authorities.
- Protect Root CA private keys with strong security controls.
- Use Intermediate CAs to issue certificates whenever possible.
- Monitor certificate expiration and revocation status.
- Revoke compromised certificates immediately.
