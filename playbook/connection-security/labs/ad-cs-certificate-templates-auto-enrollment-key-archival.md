# Lab: AD CS Certificate Templates, Auto-Enrollment, and Key Archival

## Overview

This lab demonstrated how Active Directory Certificate Services (AD CS) manages the lifecycle of enterprise certificates through certificate authority installation, customized certificate templates, Group Policy auto-enrollment, user certificate issuance, and key archival planning. These capabilities allow an organization to standardize certificate settings, distribute certificates to domain users, support authentication and encryption, and recover archived private keys when certificates are lost.

## Lab Summary

This lab follows the lifecycle of enterprise certificate management:

1. Active Directory Certificate Services was installed on PLABDM01 and configured as an enterprise root certificate authority.
2. The built-in User template was duplicated, customized as `Arnold-SecureUser`, and added to the certificate templates that the CA could issue.
3. A Group Policy Object enabled user certificate auto-enrollment, and the policy was applied to the domain with `gpupdate /force`.
4. Elizabeth Scott enrolled for the customized certificate on PLABWIN810, and the Certificate Installation Results window confirmed successful issuance.
5. The lab guide concluded with a key archival workflow involving a Key Recovery Agent, certificate approval, certificate export and import, and CA recovery-agent configuration.

## Key Takeaways

- Active Directory Certificate Services provides centralized certificate issuance and management within a Windows domain.
- Certificate templates define certificate purposes, enrollment behavior, permissions, validity periods, and subject-name settings.
- Creating a template does not automatically make it available; the certification authority must also be configured to issue it.
- Auto-enrollment permissions and Group Policy work together to distribute certificates to eligible domain users.
- Subject-name settings must match the attributes available in Active Directory user accounts.
- The customized user certificate supported client authentication, secure email, and Encrypting File System.
- `gpupdate /force` immediately refreshed the applicable Computer and User Group Policy settings.
- Successful enrollment was verified through the Certificate Installation Results window rather than assumed from policy configuration alone.
- Key archival requires a designated Key Recovery Agent and additional CA configuration because access to archived private keys is security-sensitive.
- The lab used a 2,048-bit RSA key, SHA-1 hashing, and a five-year CA validity period as specified by the provided environment.

## Workflow

### Install Active Directory Certificate Services

The Active Directory Certificate Services Certification Authority role and its management tools were installed on PLABDM01 through Windows PowerShell.

**Purpose**

- Add certificate authority services to the Windows server.
- Provide the management components needed to configure and administer the CA.
- Prepare PLABDM01 to issue certificates to domain users, computers, and services.

**Result**

- The AD CS Certification Authority feature installed successfully without requiring a server restart.

### Configure the Enterprise Root Certificate Authority

PLABDM01 was configured as an enterprise root CA using the Microsoft Software Key Storage Provider, a 2,048-bit RSA key, SHA-1 hashing, and a five-year validity period.

**Purpose**

- Establish the root of trust for certificates issued within the Practice Labs domain.
- Integrate certificate services with Active Directory.
- Define the CA key provider, key length, hashing algorithm, and validity period.

**Result**

- The enterprise root CA was created successfully.
- The `PRACTICELABS-PLABDM01-CA` node became available in the Certification Authority console.
- The server displayed the certificate templates it was authorized to issue.

### Create the Customized User Certificate Template

The built-in User certificate template was duplicated and renamed `Arnold-SecureUser`. The template was configured to prompt during enrollment, permit auto-enrollment for Authenticated Users, supersede the original User template, and exclude email attributes that were unavailable in the Practice Labs domain.

**Purpose**

- Customize certificate behavior without modifying the built-in User template.
- Allow authenticated domain users to receive the certificate through auto-enrollment.
- Replace certificates based on the original User template.
- Prevent subject-name errors caused by undefined email attributes.

**Result**

- `Arnold-SecureUser` was created with the intended purposes of Client Authentication, Secure Email, and Encrypting File System.
- Authenticated Users received the Autoenroll permission.
- The original User template was added as a superseded template.
- `Include e-mail name in subject name` and `E-mail name` were cleared.

### Add the Template to the Certification Authority

The customized template was selected in the Enable Certificate Templates window and added to the templates issued by PLABDM01.

**Purpose**

- Publish the customized template through the enterprise CA.
- Make the template available to eligible domain users.
- Connect the template configuration to the certificate issuance process.

**Result**

- `Arnold-SecureUser` appeared in the Certification Authority console as an issuable certificate template.

### Create the Certificate Auto-Enrollment Group Policy

A Group Policy Object named `Certificate Auto Enrollment` was created and linked to the Engineering organizational unit. User certificate auto-enrollment was enabled under Public Key Policies.

**Purpose**

- Automate certificate deployment to users within the Engineering OU.
- Renew expired certificates and update pending certificates.
- Remove revoked certificates from the applicable certificate stores.
- Update certificates when their underlying templates changed.
- Display notifications for certificates approaching expiration.

**Result**

- Certificate Services Client – Auto-Enrollment was enabled.
- All three required maintenance and notification settings were selected.
- The policy was linked to the Engineering OU.

### Apply the Updated Group Policy

The new Group Policy configuration was applied on PLABDC01 with `gpupdate /force`.

**Purpose**

- Refresh Computer and User Group Policy without waiting for the normal update interval.
- Propagate the new certificate auto-enrollment configuration.
- Confirm that both policy scopes processed successfully.

**Result**

- Computer Policy completed successfully.
- User Policy completed successfully.

### Enroll and Verify the User Certificate

Elizabeth Scott signed in to PLABWIN810 and opened the certificate enrollment notification from the system tray. The Certificate Enrollment wizard displayed `Arnold-SecureUser`, and the certificate was enrolled.

**Purpose**

- Confirm that the user received the auto-enrollment policy.
- Verify that the customized template was available from the enterprise CA.
- Validate the complete path from template creation to user certificate installation.

**Result**

- The Certificate Installation Results window reported `STATUS: Succeeded`.
- `Arnold-SecureUser` was enrolled and installed for Elizabeth Scott.
- The certificate was available for client authentication, secure email, and Encrypting File System.

### Configure Key Archival and Recovery

The worksheet-required run ended after successful certificate issuance verification. The lab guide’s third exercise defined the intended continuation: issuing a Key Recovery Agent certificate, manually approving its pending request, exporting and importing the certificate, and configuring the CA to archive issued private keys.

**Purpose**

- Allow authorized recovery of archived private keys when users lose access to their certificates.
- Designate a trusted administrator as the Key Recovery Agent.
- Protect recovery operations by requiring manual approval for the security-sensitive KRA certificate.
- Configure the CA to retain recoverable copies of keys for applicable certificate templates.

The guide-defined continuation consisted of:

1. Adding the Key Recovery Agent template to the CA’s issued templates.
2. Opening an MMC console with the Certificates snap-in for the current user.
3. Requesting a Key Recovery Agent certificate for the Administrator account.
4. Manually issuing the pending KRA request through the Certification Authority console.
5. Exporting the issued KRA certificate as `c:\AdminKRA.cer`.
6. Importing the certificate into the Administrator’s Personal certificate store.
7. Enabling `Archive the key` on the CA Recovery Agents tab.
8. Adding the KRA certificate and restarting Active Directory Certificate Services.

These key archival steps were documented from the complete lab guide but were not performed as part of the worksheet-required execution.

## Notes

### Certificate Template Creation and Issuance

Certificate template creation and certificate template issuance were separate actions. Duplicating and configuring the User template created `Arnold-SecureUser` in the Certificate Templates Console, but users could not request it until it was also added through `New > Certificate Template to Issue` in the Certification Authority console.

### Certificate Enrollment Flow

```text
PLABDM01
Enterprise Root CA
      |
      v
Arnold-SecureUser Template
      |
      v
Template Enabled for Issuance
      |
      v
PLABDC01
Certificate Auto Enrollment GPO
      |
      v
Engineering OU User
      |
      v
PLABWIN810
Certificate Enrollment Wizard
      |
      v
Certificate Installation Succeeded
```

### Auto-Enrollment and User Prompts

The template was configured with `Prompt the user during enrollment` because the lab required the enrollment wizard to be visible. The lab guide noted that normal automatic enrollment deployments generally do not prompt users during enrollment.

### Subject-Name Attribute Requirements

The template originally expected email-related Active Directory attributes. The Practice Labs user accounts did not define those attributes, so `Include e-mail name in subject name` and `E-mail name` were cleared to prevent the template from depending on unavailable account information.

### Key Archival Process

```text
KRA Template Enabled
        |
        v
Administrator Requests KRA Certificate
        |
        v
Request Held for Manual Approval
        |
        v
CA Administrator Issues Request
        |
        v
KRA Certificate Exported and Imported
        |
        v
KRA Added to CA Recovery Agents
        |
        v
CA Archives Recoverable Private Keys
```

Key archival and certificate backup are not identical. Key archival allows the CA to retain recoverable private-key material for qualifying certificates, while the Key Recovery Agent provides the authorization needed to recover those keys.

## Commands Used

### Install and Configure Active Directory Certificate Services

```bash
Add-WindowsFeature ADCS-Cert-Authority -IncludeManagementTools
Install-AdcsCertificationAuthority -CAType EnterpriseRootCA -CryptoProviderName "RSA#Microsoft Software Key Storage Provider" -KeyLength 2048 -HashAlgorithmName SHA1 -ValidityPeriod Years -ValidityPeriodUnits 5
exit
```

### Refresh Group Policy

```bash
gpupdate /force
```

### Identify Screenshot Evidence

```bash
echo Connor Arnold - July 29, 2026
```

## Quick Reference

| Item | Purpose |
|------|---------|
| Active Directory Certificate Services | Provides certificate authority and certificate management services in a Windows domain |
| Enterprise Root CA | Serves as the root of trust and issues certificates within Active Directory |
| Certificate Template | Defines certificate purposes, permissions, enrollment behavior, and certificate properties |
| `Arnold-SecureUser` | Customized user template created for client authentication, secure email, and EFS |
| Autoenroll Permission | Allows eligible users to receive certificates through automatic enrollment |
| Group Policy Object | Distributes certificate auto-enrollment settings to the Engineering OU |
| `gpupdate /force` | Immediately refreshes Computer and User Group Policy |
| Certificate Enrollment Wizard | Allows the user to request and install an available certificate |
| Key Recovery Agent | Authorized identity capable of recovering archived private keys |
| Key Archival | Stores recoverable copies of issued private keys through the CA |
| EFS | Uses certificates to protect files through Encrypting File System |
| Personal Certificate Store | Holds certificates issued to the current Windows user |

## Related Playbook Pages

- [Active Directory](../../connection-security/concepts/active-directory.md)
- [Authentication](../../connection-security/concepts/authentication.md)
- [Certificate Authority](../../connection-security/concepts/certificate-authority.md)
- [Digital Certificates](../../connection-security/concepts/digital-certificates.md)
- [Key Management](../../connection-security/concepts/key-management.md)
- [Public Key Infrastructure](../../connection-security/concepts/pki-public-key-infrastructure.md)
- [Encryption](../concepts/encryption.md)
- [Hashing](../concepts/hashing.md)
- [RSA](../concepts/rsa.md)
- [Active Directory Certificate Services](../concepts/active-directory-certificate-services.md) (coming soon)
- [Certificate Templates](../concepts/certificate-templates.md) (coming soon)
- [Group Policy Objects](../../system-security/concepts/group-policy-objects.md) (coming soon)
- [Key Archival and Recovery](../concepts/key-archival-and-recovery.md) (coming soon)
