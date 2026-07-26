# Lab: Configure IIS FTP Authorization Rules for Role-Based Access Control

## Overview

This lab demonstrated how to troubleshoot unauthorized folder access through an Internet Information Services (IIS) FTP site. The `Default` FTP site contained an `All Users` authorization rule that granted Read and Write permissions too broadly, allowing Human Resources to access the Customer Data folder even though only Sales and Customer Service required access. The broad rule was replaced with department-specific rules to enforce role-based access control and the principle of least privilege without modifying unrelated NTFS permissions.

## Lab Summary

This lab follows the lifecycle of IIS FTP authorization troubleshooting:

1. Locate the Customer Data folder and review its NTFS permissions.
2. Inspect the IIS FTP Authorization Rules to identify the source of the unauthorized access.
3. Remove the rule that allowed all users to read and write.
4. Create role-specific rules for Sales and Customer Service and verify the corrected configuration.

## Key Takeaways

- IIS FTP Authorization Rules control access through the FTP service.
- NTFS permissions separately control access to the underlying Windows files and folders.
- An `All Users` rule can grant access to departments that do not require the resource.
- Role-based rules are easier to manage and audit than broad user permissions.
- The principle of least privilege limits access to only the users who require it.
- The responsible access-control layer should be identified before unrelated permissions are changed.
- Configuration changes should be verified by reviewing the final authorization rules.

## Workflow

### Locate the Customer Data Folder

The CS FTP server was opened, and the physical Customer Data folder was located on the Windows Server.

**Purpose**

- Identify the resource involved in the access issue.
- Confirm the physical location of the FTP content.
- Determine which Windows and IIS settings could affect access.

**Result**

- The Customer Data folder was located at `C:\inetpub\ftproot\Customer Data`.
- The folder was provided through the `Default` FTP site in IIS Manager.

### Review the NTFS Permissions

The Advanced Security Settings for the Customer Data folder were inspected before any permissions were changed.

**Purpose**

- Determine whether the issue originated from the Windows file-system permissions.
- Review inherited permissions that could affect the folder.
- Avoid changing unrelated access-control settings before identifying the actual misconfiguration.

**Result**

- The folder inherited its permissions from `C:\inetpub`.
- `SYSTEM`, `Administrators`, and `TrustedInstaller` had Full Control.
- The Windows `Users` group had Read and Execute access.
- No NTFS permissions were changed because the documented issue involved access through the FTP service.

### Inspect the FTP Authorization Rules

The FTP Authorization Rules for the `Default` FTP site were reviewed in IIS Manager.

**Purpose**

- Determine how users were being authorized through FTP.
- Confirm why Human Resources users could access the Customer Data folder.
- Identify the exact rule responsible for the overly broad access.

**Result**

- One Allow rule applied to `All Users`.
- The rule granted both Read and Write permissions.
- The rule did not restrict access by department or role.
- Human Resources users were included because the rule applied to all FTP users.

### Remove the All Users Rule

The authorization rule granting Read and Write access to `All Users` was removed.

**Purpose**

- Eliminate access for departments that did not require the Customer Data folder.
- Remove the overly broad authorization rule.
- Prepare the FTP site for department-specific permissions.

**Result**

- The FTP site no longer granted Read and Write access to every user.
- Human Resources no longer qualified through the broad authorization rule.

### Create Department-Specific Authorization Rules

Separate Allow rules were created for the Sales and Customer Service roles. Both roles were granted Read and Write permissions.

**Purpose**

- Preserve the access required by Sales.
- Preserve the access required by Customer Service.
- Replace broad access with role-based authorization.
- Follow the principle of least privilege.

**Result**

- Sales received Read and Write access.
- Customer Service received Read and Write access.
- Human Resources was not included in either authorization rule.

### Verify the Final Configuration

The FTP Authorization Rules were reviewed again after both department-specific rules were added.

**Purpose**

- Confirm that the `All Users` rule had been removed.
- Verify that the required departments retained access.
- Ensure that the corrected configuration matched the stated access requirement.

**Result**

- The final configuration contained separate Allow rules for Sales and Customer Service.
- Both roles had Read and Write permissions.
- The `All Users` rule was no longer present.
- Human Resources had no matching Allow rule for the FTP site.

## Notes

### IIS FTP Authorization and NTFS Permissions

IIS FTP Authorization Rules and NTFS permissions are separate access-control layers. IIS determines who may access content through the FTP service and which FTP operations are permitted. NTFS controls access to the underlying files and folders through Windows.

An FTP user generally must satisfy both layers. An IIS Allow rule does not override restrictive NTFS permissions, and NTFS permission alone does not guarantee access through IIS. In this lab, the overly broad IIS rule caused the unauthorized FTP access, so the inherited NTFS permissions were reviewed but left unchanged.

### FTP Authorization Flow

```text
Authenticated FTP User
          |
          v
IIS FTP Authorization Rules
          |
    +-----+-----------------------+----------------------+
    |                             |                      |
    v                             v                      v
Sales Role              Customer Service Role   Human Resources
Read and Write          Read and Write          No Matching Allow Rule
Allowed                 Allowed                 Access Denied by IIS
```

### Role-Based Access Control

The corrected configuration assigned permissions to department roles rather than individual users or all users. This follows Role-Based Access Control because access is determined by the user's organizational role.

### Principle of Least Privilege

The original `All Users` rule granted permissions beyond the business requirement. Replacing it with Sales and Customer Service rules limited FTP access to the departments that required the Customer Data folder while removing unnecessary Human Resources access.

## Commands Used

No command-line commands were required. The configuration was inspected and corrected through Windows graphical management interfaces.

### Inspect FTP Authorization Rules

```text
IIS Manager
Sites > Default > FTP Authorization Rules
```

### Inspect NTFS Permissions

```text
C:\inetpub\ftproot\Customer Data
Properties > Security > Advanced
```

## Quick Reference

| Item | Purpose |
|------|---------|
| `C:\inetpub\ftproot\Customer Data` | Physical location of the Customer Data folder |
| IIS Manager | Manage Windows web and FTP services |
| `Default` FTP site | Provide FTP access to the server content |
| FTP Authorization Rules | Allow or deny FTP access for users and roles |
| `All Users` | Apply a rule broadly to every qualifying FTP user |
| Sales role | Authorized department with Read and Write access |
| Customer Service role | Authorized department with Read and Write access |
| Human Resources | Department excluded from FTP access |
| NTFS permissions | Control Windows file and folder access |
| Role-Based Access Control | Assign permissions according to organizational roles |
| Least privilege | Grant only the access required to perform a task |

## Related Playbook Pages

- [Authorization](../concepts/authorization.md)
- [Access Control Models](../concepts/access-control-models.md)
- [Ports and Port Numbers](../concepts/ports-and-port-numbers.md)
- [File Transfer Protocol (FTP)](../concepts/ftp-file-transfer-protocol.md) (coming soon)
- [Internet Information Services (IIS) Manager](../../system-security/tools/iis-internet-information-services-manager.md) (coming soon)
- [NTFS Permissions](../../system-security/concepts/ntfs-permissions.md) (coming soon)
