# Lab: Install and Configure Active Directory Certificate Services

## Overview

This lab demonstrates how to deploy and manage an Enterprise Root Certification Authority using Active Directory Certificate Services (AD CS). It covers installing and configuring the Certification Authority, issuing and revoking user certificates, and backing up the Certification Authority to support certificate lifecycle management and disaster recovery within a Windows domain.

## Lab Summary

This lab follows the lifecycle of deploying and maintaining an Enterprise Root Certification Authority:

1. Install Active Directory Certificate Services.
2. Configure an Enterprise Root Certification Authority.
3. Verify the Certification Authority installation.
4. Request and issue a user certificate.
5. Revoke the issued certificate.
6. Verify certificate revocation.
7. Back up the Certification Authority.
8. Export the Certification Authority configuration.

## Key Takeaways

- Active Directory Certificate Services provides Microsoft's Public Key Infrastructure (PKI) for Windows environments.
- Enterprise Root Certification Authorities integrate directly with Active Directory to issue trusted certificates.
- Certificate revocation prevents compromised or invalid certificates from being trusted before they expire.
- Certificate Revocation Lists (CRLs) distribute revocation information throughout the PKI.
- Certification Authority backups protect the private key, certificate database, and configuration for disaster recovery.
- Certutil provides command-line administration and backup capabilities for AD CS.
- Proper CA backups are critical to restoring trust after hardware or system failures.

## Workflow

### Install Active Directory Certificate Services

Installed the Active Directory Certificate Services server role using Server Manager. Added the Certification Authority and Online Responder role services along with the required IIS components.

**Purpose**

- Deploy Microsoft's Public Key Infrastructure service.
- Enable certificate issuance and management.
- Prepare the server to function as a Certification Authority.

### Configure the Enterprise Root Certification Authority

Configured the server as an Enterprise Root Certification Authority using the default cryptographic provider, key length, hashing algorithm, CA name, database location, and five-year validity period.

**Purpose**

- Establish the root of trust for the domain.
- Create the Certification Authority's cryptographic identity.
- Configure the Certification Authority database and private key.

**Result**

- The Enterprise Root Certification Authority was successfully configured and operational.

### Verify the Certification Authority

Opened the Certification Authority management console to verify that the Certification Authority was functioning correctly.

**Purpose**

- Confirm that Certificate Services installed successfully.
- Verify that the Certification Authority was ready to issue certificates.

**Result**

- The Certification Authority console displayed a healthy Enterprise Root Certification Authority.

### Request a User Certificate

Requested a User certificate through the Certificates MMC snap-in while logged in as a domain user.

**Purpose**

- Demonstrate certificate enrollment.
- Verify that the Certification Authority could issue certificates to Active Directory users.

**Result**

- A User certificate was successfully issued.

### Revoke the User Certificate

Located the issued certificate in the Certification Authority console and revoked it using the **Key Compromise** revocation reason.

**Purpose**

- Demonstrate certificate lifecycle management.
- Prevent a compromised certificate from being trusted.

**Result**

- The certificate appeared in the **Revoked Certificates** container.

This demonstrates how revoked certificates are tracked and prevented from being trusted before they expire.

### Back Up the Certification Authority

Created a full backup of the Certification Authority using the Certification Authority Backup Wizard.

The backup included:

- Private key
- CA certificate
- Certificate database
- Certificate database log

**Purpose**

- Protect the Certification Authority against data loss.
- Preserve the components required for disaster recovery.

**Result**

- A complete Certification Authority backup was successfully created.

### Back Up the Certification Authority Using Certutil

Performed a command-line backup of the Certification Authority using Certutil.

**Purpose**

- Demonstrate command-line administration of AD CS.
- Create a backup using Microsoft's PKI management utility.

**Result**

- The Certification Authority database was successfully backed up.

### Export the Certification Authority Configuration

Exported the Certification Authority registry configuration to a `.reg` file.

**Purpose**

- Preserve the Certification Authority configuration.
- Support complete restoration of the Certification Authority.

**Result**

- The Certification Authority configuration was successfully exported.

## Notes

### Enterprise Root Certification Authority

An Enterprise Root Certification Authority integrates directly with Active Directory. It automatically publishes certificates and Certificate Revocation Lists (CRLs), allowing domain users and computers to trust certificates issued by the Certification Authority.

### Certification Authority Lifecycle

```text
Install AD CS
      │
      ▼
Configure Enterprise Root CA
      │
      ▼
Issue User Certificate
      │
      ▼
Certificate Used
      │
      ▼
Certificate Revoked
      │
      ▼
CRL Updated
      │
      ▼
Back Up CA
      │
      ▼
Export CA Configuration
```

### Certification Authority Backup

A complete Certification Authority backup includes:

- Private key
- CA certificate
- Certificate database
- Database logs
- Registry configuration

Together, these components allow the Certification Authority to be fully restored after hardware failure, corruption, or accidental data loss.

## Commands Used

### Back Up the Certification Authority

```cmd
certutil -backup C:\BackupCA2
```

### Export the Certification Authority Configuration

```cmd
reg export "HKLM\System\CurrentControlSet\Services\CertSvc\Configuration" C:\BackupCA1\CAConfig.reg
```

## Quick Reference

| Item | Purpose |
|------|---------|
| Active Directory Certificate Services (AD CS) | Provides Microsoft's Public Key Infrastructure |
| Enterprise Root Certification Authority | Trusted root Certification Authority integrated with Active Directory |
| Certification Authority (CA) | Issues, manages, and revokes digital certificates |
| Online Responder | Provides certificate status information using OCSP |
| User Certificate | Authenticates users and computers within the domain |
| Certificate Revocation | Invalidates certificates before expiration |
| Certificate Revocation List (CRL) | Publishes revoked certificates to clients |
| Certutil | Command-line utility for administering and backing up AD CS |
| Certification Authority Backup | Protects the CA database, certificate, and private key |
| Registry Export | Preserves the Certification Authority configuration for recovery |

## Related Playbook Pages

- [Active Directory Certificate Services (AD CS)](../concepts/active-directory-certificate-services.md) (coming soon)
- [Certificate Authority (CA)](../../connection-security/concepts/certificate-authority.md)
- [Certificate Revocation Lists (CRLs)](../../connection-security/concepts/certificate-revocation-lists-crls.md) (coming soon)
- [Online Certificate Status Protocol (OCSP)](../../connection-security/concepts/online-certificate-status-protocol-ocsp.md) (coming soon)
- [Digital Certificates](../../connection-security/concepts/digital-certificates.md)
- [Public Key Infrastructure (PKI)](../../connection-security/concepts/pki-public-key-infrastructure.md)
- [Certutil](../tools/certutil.md) (coming soon)
