# Lab: Install and Configure Active Directory Certificate Services

## Overview

This lab demonstrates how to install and configure Active Directory Certificate Services (AD CS) as an Enterprise Root Certification Authority in a Windows domain environment. It also covers requesting and revoking user certificates, publishing certificate revocation information, and backing up the Certification Authority for disaster recovery.

### Objective

- Install and configure Active Directory Certificate Services.
- Configure an Enterprise Root Certification Authority.
- Request and issue a user certificate.
- Revoke an issued certificate.
- Verify certificate revocation.
- Perform Certificate Authority backups using both the graphical interface and Certutil.
- Export the Certificate Authority configuration for recovery.

## Key Takeaways

- Active Directory Certificate Services provides a Public Key Infrastructure (PKI) for Windows domains.
- Enterprise Root CAs issue trusted certificates to users and computers within Active Directory.
- Certificate revocation prevents compromised or invalid certificates from being trusted.
- Certificate Revocation Lists (CRLs) distribute revocation information throughout the environment.
- Backing up the CA database, private key, and configuration is essential for disaster recovery.
- Certutil provides command-line administration and backup capabilities for AD CS.

## Workflow

### Install Active Directory Certificate Services

Installed the Active Directory Certificate Services role using Server Manager. Added the Certification Authority and Online Responder role services, along with the required IIS components.

### Configure the Enterprise Root CA

Configured the server as an Enterprise Root Certification Authority using the default cryptographic settings, CA name, database location, and five-year validity period.

### Verify Certificate Services

Opened the Certification Authority management console to verify that the Certification Authority was successfully configured and operational.

### Request a User Certificate

Logged in as a domain user and requested a User certificate through the Certificates MMC snap-in. Successfully enrolled and issued the certificate.

### Revoke the Certificate

Located the issued certificate within the Certification Authority console and revoked it using the **Key Compromise** revocation reason. Verified that it appeared under **Revoked Certificates**.

### Backup the Certificate Authority

Created a full backup of the Certification Authority using the Certification Authority Backup Wizard, including:

- Private key and CA certificate
- Certificate database
- Certificate database log

### Backup Using Certutil

Performed a command-line backup of the Certification Authority using Certutil.

### Export the CA Configuration

Exported the Certificate Services registry configuration to a `.reg` file for recovery purposes.

## Notes

### Enterprise Root CA

An Enterprise Root Certification Authority integrates directly with Active Directory and automatically publishes certificates and CRLs to the domain.

### Certificate Revocation

Revoking a certificate prevents it from being trusted even if it has not expired. The revocation reason identifies why the certificate was invalidated.

### Certificate Revocation Lists (CRLs)

CRLs allow clients to determine whether a certificate has been revoked before trusting it during authentication or encrypted communications.

### CA Backup Components

A complete Certificate Authority backup includes:

- Private key
- CA certificate
- Certificate database
- Database logs
- CA configuration

Without these components, a failed CA cannot be fully restored.

## Commands Used

### Backup the Certificate Authority

```cmd
certutil -backup C:\BackupCA2
```

### Export the CA Configuration

```cmd
reg export "HKLM\System\CurrentControlSet\Services\CertSvc\Configuration" C:\BackupCA1\CAConfig.reg
```

## Related Playbook Pages

- [Active Directory Certificate Services (AD CS)](../concepts/active-directory-certificate-services.md) (coming soon)
- [Certificate Authority (CA)](../../connection-security/concepts/certificate-authority.md) 
- [Certificate Revocation Lists (CRLs)](../../connection-security/concepts/certificate-revocation-lists-crls.md) 
- [Online Certificate Status Protocol (OCSP)](../../connection-security/concepts/online-certificate-status-protocol-ocsp.md)
- [Digital Certificates](../../connection-security/concepts/digital-certificates.md)
- [Public Key Infrastructure (PKI)](../../connection-security/concepts/pki-public-key-infrastructure.md)
- [Certutil](../concepts/certutil.md)
