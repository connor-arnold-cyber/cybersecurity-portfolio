# Lab: Cross-Platform Automation and Active Directory User Provisioning

CYB-300 6-2

## Overview

This lab demonstrated how Bash and Windows PowerShell scripts can automate repetitive administrative operations across Linux and Windows environments. The workflow included preparing files for backup, creating a Linux archive script, mapping a shared network drive, and provisioning an Active Directory user account, illustrating how automation can improve consistency and reduce manual administrative effort.

## Lab Summary

This lab follows the lifecycle of cross-platform administrative automation:

1. Ten sample files and a backup directory were created and verified on an AlmaLinux server.
2. A Bash script was created, assigned executable permissions, and used to archive the Documents directory.
3. A Marketing folder was created and shared from a Windows Server domain controller.
4. A PowerShell script was created and executed to map the shared Marketing folder as the K: drive.
5. A Marketing Organizational Unit was created in Active Directory.
6. A PowerShell script collected user information and provisioned the Subi user account.
7. The mapped drive and newly created Active Directory account were verified through graphical management tools.

## Key Takeaways

- Bash scripts can automate Linux file-management and backup operations.
- The shebang identifies which interpreter should execute a Linux script.
- Linux scripts require executable permissions before they can be run directly.
- The `tar` utility can package directories and files into a single archive.
- PowerShell can automate Windows administrative operations across local and domain systems.
- `New-PSDrive` can create a persistent drive mapping to a shared network folder.
- The Active Directory PowerShell module supports automated Organizational Unit and user creation.
- Interactive prompts allow one script to provision accounts using different user information.
- Automated account provisioning reduces repetitive work and improves configuration consistency.
- Script results should be verified through command output and administrative management consoles.

## Workflow

### Prepare the Linux Files and Backup Directory

Ten empty files named `acidoc1` through `acidoc10` were created inside the `Documents` directory. A separate `Backup` directory was then created in the user’s home directory.

**Purpose**

- Provide sample files for the backup operation.
- Establish a destination directory for the archive.
- Verify the source files and directory structure before scripting the backup.

**Result**

- The `Documents` directory contained all ten required files.
- The `Backup` directory appeared in the user’s home-directory listing.

### Create the Linux Backup Script

An `acibackup.sh` file was created and edited with Vim. The script used Bash and the `tar` utility to archive the user’s entire `Documents` directory into the `Backup` directory.

**Purpose**

- Automate a repetitive backup operation.
- Demonstrate the basic structure of a Bash script.
- Replace a manually entered archive command with a reusable script.

**Result**

- The completed script contained a Bash shebang and a `tar` command.
- The script targeted `/home/aciadmin/Documents`.
- The archive destination was `/home/aciadmin/Backup/acibackup.tar`.

### Assign and Verify Script Permissions

Executable permissions were added to `acibackup.sh` using `chmod`. The script’s permissions and contents were then displayed for verification.

**Purpose**

- Allow the script to be executed directly from the terminal.
- Confirm that the executable permission had been applied.
- Verify that the script contained the intended backup command.

**Result**

- The script permissions displayed as `-rwxr-xr-x`.
- The script contents showed the correct shebang and archive command.

### Execute the Linux Backup

The completed Bash script was executed from the user’s home directory. The verbose `tar` option displayed each file as it was added to the archive.

**Purpose**

- Perform the automated backup operation.
- Confirm that the script could execute successfully.
- Create a reusable archive of the Documents directory.

**Result**

- The ten sample files were processed by the script.
- The backup archive was created in the designated `Backup` directory.

### Configure the Marketing Network Share

A folder named `Marketing` was created on the `C:` drive of the ACIDC01 domain controller. Advanced Sharing was enabled so the folder could be accessed across the network as `\\ACIDC01\Marketing`.

**Purpose**

- Provide a centralized network location for the Marketing department.
- Establish the shared resource required by the drive-mapping script.
- Demonstrate the relationship between server-side sharing and client-side drive mapping.

**Result**

- The Marketing folder was shared from ACIDC01.
- The network path became available as `\\ACIDC01\Marketing`.

### Create the PowerShell Drive-Mapping Script

A PowerShell script named `mapdrive.ps1` was created on ACIWIN11. The script used `New-PSDrive` to map the Marketing share to drive letter `K:`.

**Purpose**

- Automate a common workstation configuration task.
- Create a reusable method for connecting users to a departmental share.
- Demonstrate persistent PowerShell drive mapping.

**Result**

- Drive `K:` was mapped to `\\ACIDC01\Marketing`.
- The mapped drive used the FileSystem PowerShell provider.
- The drive appeared in File Explorer.

### Create the Marketing Organizational Unit

A Marketing Organizational Unit was created inside the `aciplab.com` domain with the Active Directory PowerShell module.

**Purpose**

- Provide a logical container for Marketing user accounts.
- Support organized administration and future policy assignment.
- Establish the destination path required by the user-provisioning script.

**Result**

- The Marketing Organizational Unit appeared under `aciplab.com`.
- The Organizational Unit was available as the target location for the new account.

### Create the Active Directory User-Provisioning Script

A PowerShell script named `createuser.ps1` was created on ACIDC01. The script imported the Active Directory module, requested account information interactively, and passed the responses to `New-ADUser`.

**Purpose**

- Automate Active Directory user provisioning.
- Reduce the number of manual steps required to create an account.
- Allow the same script to be reused with different user information.

**Result**

- The script accepted the user’s name, surname, account name, User Principal Name, and password.
- The account was enabled immediately.
- The user was configured to change the password at the next sign-in.
- The account was placed in the Marketing Organizational Unit.

### Verify the Subi User Account

Active Directory Users and Computers was opened and the Marketing Organizational Unit was selected. The Subi account was visible inside the Organizational Unit.

**Purpose**

- Confirm that the PowerShell script created the intended account.
- Verify that the account was placed in the correct Organizational Unit.
- Compare scripted account creation with graphical Active Directory administration.

**Result**

- The Subi user appeared inside the Marketing Organizational Unit.
- PowerShell showed the values entered during script execution.
- The automated provisioning operation completed successfully.

## Notes

### Cross-Platform Script Types

The lab used two scripting environments:

| Operating System | Shell | Script Extension | Lab Use |
|---|---|---|---|
| AlmaLinux | Bash | `.sh` | Archive the Documents directory |
| Windows | PowerShell | `.ps1` | Map a network drive and create an Active Directory user |

Although Bash and PowerShell use different syntax, both environments allowed a sequence of administrative commands to be stored and executed repeatedly.

### Linux Backup Flow

```text
Documents Directory
        |
        | acibackup.sh
        v
tar Archive Process
        |
        v
Backup/acibackup.tar
```

The script used an absolute source path and destination path. Absolute paths allowed the script to locate the intended directories without depending on the terminal’s current working directory.

### Drive-Mapping Flow

```text
ACIDC01
C:\Marketing
     |
     | Advanced Sharing
     v
\\ACIDC01\Marketing
     |
     | mapdrive.ps1
     v
ACIWIN11
K: Drive
```

The folder first had to be shared from ACIDC01 before the PowerShell script on ACIWIN11 could map it as a persistent drive.

### Active Directory Provisioning Flow

```text
createuser.ps1
      |
      | Read-Host prompts
      v
New-ADUser
      |
      v
aciplab.com
      |
      v
Marketing Organizational Unit
      |
      v
Subi User Account
```

The script used `Read-Host` to collect account information when it ran. The collected values were passed directly into `New-ADUser`, allowing the script to be reused without editing the source code for every account.

### Password Handling

The password prompt used `Read-Host -AsSecureString`, which prevented the entered password from being displayed as readable text in the PowerShell window. The account was also configured with `-ChangePasswordAtLogon $true`, requiring the user to establish a new password at the first sign-in.

## Commands Used

### Create and Verify the Linux Files

```bash
touch Documents/acidoc{1..10}
ls -l Documents/
mkdir Backup
ls -l
```

### Create the Linux Backup Script

```bash
touch acibackup.sh
vim acibackup.sh
```

```bash
#!/bin/bash
tar cfv /home/aciadmin/Backup/acibackup.tar /home/aciadmin/Documents
```

```bash
:wq
```

### Assign and Verify Script Permissions

```bash
chmod +x acibackup.sh
ls -l acibackup.sh
cat acibackup.sh
```

### Execute the Linux Backup Script

```bash
./acibackup.sh
```

### Create the PowerShell Drive-Mapping Script

```bash
notepad.exe mapdrive.ps1
```

```bash
New-PSDrive -Name K -PSProvider FileSystem -Root "\\ACIDC01\Marketing" -Persist -Scope Global
```

### Permit and Execute the PowerShell Script

```bash
Set-ExecutionPolicy Unrestricted
.\mapdrive.ps1
```

### Create the Marketing Organizational Unit

```bash
New-ADOrganizationalUnit -Name Marketing -Path "DC=ACIPLAB,DC=COM"
```

### Create the Active Directory User Script

```bash
notepad.exe createuser.ps1
```

```bash
Import-Module ActiveDirectory
New-ADUser -Name (Read-Host "Enter Name") -GivenName (Read-Host "Enter Given Name") -Surname (Read-Host "Enter Surname") -SamAccountName (Read-Host "Enter SamAccountName") -UserPrincipalName (Read-Host "Enter UPN eg @aciplab.com") -Path "OU=Marketing,DC=ACIPLAB,DC=COM" -AccountPassword (Read-Host -AsSecureString "Enter Secure Password") -ChangePasswordAtLogon $true -Enabled $true
```

### Execute the User-Provisioning Script

```bash
.\createuser.ps1
```

```bash
Enter Name: Subi
Enter Given Name: Subi
Enter Surname: P
Enter SamAccountName: Subi.p
Enter UPN eg @aciplab.com: subi.p@aciplab.com
Enter Secure Password: Passw0rd
```

## Quick Reference

| Item | Purpose |
|------|---------|
| `touch` | Creates empty files or updates file timestamps |
| Brace expansion `{1..10}` | Generates a sequential range of values |
| `ls -l` | Displays detailed file and permission information |
| `vim` | Creates and edits text-based script files |
| `#!/bin/bash` | Identifies Bash as the script interpreter |
| `tar cfv` | Creates an archive and displays processed files |
| `chmod +x` | Adds executable permission to a file |
| `.sh` | Common Bash script file extension |
| `.ps1` | PowerShell script file extension |
| `New-PSDrive` | Creates a PowerShell drive mapping |
| `-Persist` | Makes a mapped drive visible outside the current PowerShell session |
| `Set-ExecutionPolicy` | Controls whether PowerShell scripts may execute |
| `Import-Module ActiveDirectory` | Loads Active Directory PowerShell commands |
| `New-ADOrganizationalUnit` | Creates an Active Directory Organizational Unit |
| `New-ADUser` | Creates an Active Directory user account |
| `Read-Host` | Collects interactive input from the operator |
| `-AsSecureString` | Collects sensitive input without displaying readable text |
| `-ChangePasswordAtLogon` | Requires a password change during the first sign-in |
| Active Directory Users and Computers | Graphically manages and verifies directory objects |

## Related Playbook Pages

- [Active Directory](../../connection-security/concepts/active-directory.md)
- [Bash Cheat Sheet](../tools/bash-cheat-sheet.md)
- [Bash Scripting Guide](../tools/bash-scripting-guide.md)
- [PowerShell Cheat Sheet](../tools/powershell-cheat-sheet.md)
- [Automation and Orchestration](../concepts/automation-and-orchestration.md) (coming soon)
