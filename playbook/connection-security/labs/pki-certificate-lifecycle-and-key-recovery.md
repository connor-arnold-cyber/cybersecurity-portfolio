# Lab: Public Key Infrastructure Certificate Lifecycle and Key Recovery

## Overview

This lab demonstrated how a public key infrastructure (PKI) supports certificate creation, trust delegation, certificate enrollment, revocation management, template-based deployment, and private-key recovery. It combined OpenSSL-based self-signed certificate generation with Microsoft Active Directory Certificate Services (AD CS) to show how certificates move through a managed lifecycle from issuance through recovery.

## Lab Summary

This lab follows the lifecycle of public key infrastructure certificate management:

1. Reviewed core PKI concepts, certificate types, trust models, certificate attributes, and certificate file formats.
2. Generated a private key, certificate signing request, and self-signed certificate with OpenSSL.
3. Installed and configured an enterprise root certificate authority on PLABDC01 and an enterprise subordinate certificate authority on PLABDM01.
4. Requested a user certificate from the subordinate certificate authority and reviewed the intended certificate revocation and Certificate Revocation List distribution process.
5. Reviewed the intended certificate-template customization and Group Policy auto-enrollment workflow.
6. Requested, approved, exported, imported, and verified a Key Recovery Agent certificate for the Administrator account.
7. Reviewed the final configuration required to enable certificate key archival on the subordinate certificate authority.

## Key Takeaways

- A public key infrastructure combines certificate authorities, certificates, keys, policies, and trust relationships into a managed security system.
- A root certificate authority anchors trust and can delegate operational certificate issuance to subordinate certificate authorities.
- Self-signed certificates are useful for internal testing but are not automatically trusted by external systems.
- A certificate signing request contains identity information and a public key that can be incorporated into an issued certificate.
- Certificate Revocation Lists prevent revoked certificates from continuing to authenticate users or devices.
- Certificate templates standardize certificate purposes, enrollment permissions, validity settings, and deployment behavior.
- Group Policy can automate certificate enrollment for domain users and computers.
- Key Recovery Agent certificates are security-sensitive because they permit recovery of archived private keys.
- Key archival protects access to encrypted data when a user's private key is lost or corrupted.
- Recovery authority should be limited to specifically trusted administrators.

## Workflow

### Review PKI Fundamentals

The lab began by reviewing public key infrastructure components, certificate authorities, registration authorities, Certificate Revocation Lists, Online Certificate Status Protocol, certificate signing requests, certificate attributes, trust models, key escrow, certificate chaining, certificate types, and certificate formats.

**Purpose**

- Establish the terminology required to understand certificate trust and management.
- Explain how certificates are issued, validated, revoked, and chained to a trusted root.
- Distinguish certificate purposes and common certificate file formats.

### Generate a Self-Signed Certificate

A protected directory was created on PLABKALI, and OpenSSL was used to generate a 2048-bit RSA private key, create a certificate signing request, and sign the request with the private key to produce `plab.crt`.

**Purpose**

- Demonstrate the relationship between a private key, certificate signing request, and certificate.
- Create a certificate without relying on an external certificate authority.
- Provide a test certificate suitable for internal or lab use.

**Result**

- The `plab.crt` self-signed certificate was successfully generated and verified in `/etc/ssl/private/plab`.

### Install and Configure the Enterprise Root Certificate Authority

Active Directory Certificate Services and Online Responder were installed on PLABDC01. The server was configured as an enterprise root certificate authority with a newly generated private key.

**Purpose**

- Establish the root of trust for the Practice Labs domain.
- Integrate certificate services with Active Directory.
- Provide a parent certificate authority for subordinate certificate authorities.

**Result**

- Certification Authority and Online Responder configuration completed successfully on PLABDC01.

### Install and Configure the Enterprise Subordinate Certificate Authority

Active Directory Certificate Services and Online Responder were installed on PLABDM01. The server was configured as an enterprise subordinate certificate authority and received its authority from `practicelabs-PLABDC01-CA`.

**Purpose**

- Delegate routine certificate issuance away from the root certificate authority.
- Reduce direct operational use of the root certificate authority.
- Create a scalable certificate authority hierarchy.

**Result**

- Certification Authority and Online Responder configuration completed successfully on PLABDM01.
- PLABDM01 appeared as an enterprise subordinate certificate authority beneath the PLABDC01 root.

### Request a User Certificate from the Subordinate Certificate Authority

The Certificates snap-in was added to Microsoft Management Console on PLABWIN10 for the Jan.Regus account. The User certificate template was selected, and the subordinate certificate authority was chosen as the issuing server.

**Purpose**

- Demonstrate certificate enrollment for an Active Directory user.
- Confirm that the subordinate certificate authority could issue user certificates.
- Preserve the root certificate authority for higher-level trust functions.

**Result**

- The certificate enrollment interface displayed both the enterprise root and subordinate certificate authorities.
- The user certificate request was directed to `practicelabs-PLABDM01-CA`.

### Manage Certificate Revocation and CRL Distribution

The complete lab workflow called for verifying the issued certificate on PLABDM01, revoking it for key compromise, publishing a new Certificate Revocation List, configuring a network distribution path, and restricting certificate-manager permissions.

**Purpose**

- Prevent a revoked certificate from continuing to authenticate a user.
- Distribute revocation information to other certificate authorities and clients.
- Limit certificate administration to authorized groups or individuals.

### Review and Customize Certificate Templates

The complete lab workflow called for reviewing existing certificate templates, duplicating the User template as `SecureUser`, configuring enrollment behavior and permissions, defining superseded templates, and making the new template available for issuance.

**Purpose**

- Standardize certificate settings for users and devices.
- Control certificate purposes, permissions, subject information, and validity behavior.
- Prepare a certificate template for automated domain deployment.

### Configure Certificate Auto-Enrollment

The complete lab workflow called for creating a Group Policy Object named `Certificate Auto Enrollment`, enabling Certificate Services Client Auto-Enrollment, refreshing Group Policy, and confirming that Jan.Regus received a SecureUser certificate.

**Purpose**

- Automate certificate deployment through Active Directory Group Policy.
- Reduce manual enrollment work in larger organizations.
- Renew, update, and remove certificates according to policy.

### Enable and Issue a Key Recovery Agent Certificate

The Key Recovery Agent template was enabled on PLABDM01. The Administrator account requested the certificate, the pending request was manually issued, and the certificate was exported as `C:\AdminKRA.cer` and imported into the Administrator's Personal certificate store.

**Purpose**

- Authorize a trusted administrator to recover archived private keys.
- Require manual approval for a security-sensitive certificate.
- Make the Key Recovery Agent certificate available for certificate-authority recovery configuration.

**Result**

- A certificate issued to Administrator with the intended purpose `Key Recovery Agent` was available in the Personal certificate store.
- The certificate was issued by `practicelabs-PLABDM01-CA`.

### Configure the Certificate Authority for Key Archival

The final lab workflow called for opening the Recovery Agents tab in the PLABDM01 certificate authority properties, selecting `Archive the key`, adding the Administrator's Key Recovery Agent certificate, and restarting Active Directory Certificate Services.

**Purpose**

- Preserve recoverable copies of private keys for eligible issued certificates.
- Restore access to encrypted data when a user's private key is lost or corrupted.
- Restrict recovery capability to approved recovery agents.

## Notes

### Execution Scope

The worksheet required evidence for self-signed certificate creation, the root and subordinate certificate authority hierarchy, and the Administrator Key Recovery Agent certificate. Those stages were completed. The Certificate Revocation List distribution, certificate-manager restriction, certificate-template customization, Group Policy auto-enrollment, and final `Archive the key` configuration stages were documented from the complete lab workflow but were not executed during the shortened worksheet path.

### PKI Trust Hierarchy

```text
PLABDC01
Enterprise Root CA
        |
        | signs and delegates trust
        v
PLABDM01
Enterprise Subordinate CA
        |
        | issues and manages certificates
        v
Users, computers, templates, revocation, and recovery services
```

### Key Recovery Process

```text
Administrator requests Key Recovery Agent certificate
                         |
                         v
Certificate request remains pending
                         |
                         v
CA administrator manually issues certificate
                         |
                         v
Certificate is exported and imported into Personal store
                         |
                         v
CA can be configured to archive keys for approved recovery
```

### Troubleshooting

- PLABDC01 was initially configured with the Subordinate CA option, which caused the wizard to request a parent certificate authority. Returning to the CA Type page and selecting Root CA corrected the configuration.
- PLABWIN10 initially displayed `Certificate types are not available`. Running `gpupdate /force` as an administrator refreshed domain policy and made the certificate templates available.
- OpenSSL displayed `Ignoring -days; not generating a certificate` during certificate signing request creation because the request itself did not receive a validity period. The certificate validity was applied later by the `openssl x509` command.

## Commands Used

### Generate the Self-Signed Certificate

```bash
mkdir -p /etc/ssl/private/plab
cd /etc/ssl/private/plab
openssl genrsa -des3 -out plab.key 2048
openssl req -new -days 3650 -key plab.key -out plab.csr
openssl x509 -in plab.csr -out plab.crt -req -signkey plab.key -days 3650
ls -l plab.crt
```

### Open Microsoft Management Console and Refresh Group Policy

```bash
mmc
gpupdate /force
```

### Screenshot Identity Evidence

```bash
echo "Connor Arnold"
echo Connor Arnold
```

### Lab-Prescribed Commands Not Executed in the Shortened Submission Path

```bash
openssl version
clear
chmod -R 700 /etc/ssl/private/plab
openssl rsa -in plab.key -out plab.key
chmod 400 plab.*
ln -s plab.key web.plab.key
ln -s plab.crt web.plab.crt
ls -l
```

## Quick Reference

| Item | Purpose |
|------|---------|
| Public Key Infrastructure (PKI) | Manages certificates, keys, trust, policies, issuance, revocation, and recovery |
| Root Certificate Authority | Anchors the certificate trust hierarchy |
| Subordinate Certificate Authority | Performs delegated certificate issuance and management |
| Active Directory Certificate Services (AD CS) | Provides Microsoft enterprise certificate-authority services |
| Online Responder | Supplies online certificate-status information |
| Certificate Signing Request (CSR) | Submits identity information and a public key for certificate issuance |
| Self-Signed Certificate | Certificate signed by its own private key rather than an external authority |
| Certificate Revocation List (CRL) | Publishes certificates that should no longer be trusted |
| Certificate Template | Defines certificate purpose, permissions, settings, and enrollment behavior |
| Auto-Enrollment | Automatically deploys certificates through Group Policy |
| Key Archival | Stores recoverable copies of eligible private keys |
| Key Recovery Agent (KRA) | Authorized identity used to recover archived private keys |
| `plab.key` | RSA private key generated with OpenSSL |
| `plab.csr` | Certificate signing request generated from the private key |
| `plab.crt` | Self-signed certificate generated from the request and private key |
| `C:\AdminKRA.cer` | Exported Administrator Key Recovery Agent certificate |

## Related Playbook Pages

### Concepts

- [Active Directory](../concepts/active-directory.md)
- [Active Directory Certificate Services (AD CS)](../concepts/active-directory-certificate-services.md) (coming soon)
- [Asymmetric Encryption](../../data-security/concepts/asymmetric-encryption.md)
- [Certificate Authority](../concepts/certificate-authority.md)
- [Certificate Revocation Lists (CRLs)](../concepts/certificate-revocation-lists-crls.md) (coming soon)
- [Certificate Signing Requests (CSRs)](../concepts/csr-certificate-signing-requests.md)
- [Digital Certificates](../concepts/digital-certificates.md)
- [Digital Signatures](../../data-security/concepts/digital-signatures.md)
- [Key Archival](../concepts/key-archival.md) (coming soon)
- [Key Management](../concepts/key-management.md)
- [Key Recovery Agent](../concepts/key-recovery-agent.md) (coming soon)
- [Online Certificate Status Protocol (OCSP)](../concepts/online-certificate-status-protocol-ocsp.md) (coming soon)
- [PKCS: Public Key Cryptography Standards](../concepts/pkcs-public-key-cryptography-standards.md)
- [Public Key Infrastructure (PKI)](../concepts/pki-public-key-infrastructure.md)
- [RSA](../../data-security/concepts/rsa.md)
- [Self-Signed Certificates](../concepts/self-signed-certificates.md) (coming soon)
- [Transport Layer Security (TLS)](../concepts/tls-transport-layer-security.md)
- [OpenSSL](../tools/openssl.md) (coming soon)
