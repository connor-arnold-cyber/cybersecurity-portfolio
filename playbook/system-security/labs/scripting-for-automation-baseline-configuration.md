# Lab: Scripting for Automation Baseline Configuration

## Overview

This lab demonstrates how to automate common Linux system administration tasks using Bash. A baseline configuration script was created to standardize newly deployed systems by configuring system settings, creating users and groups, collecting process information, and exporting command history. Automating these tasks improves consistency, reduces manual errors, and simplifies system provisioning.

## Lab Summary

This lab follows the lifecycle of creating a baseline system configuration:

1. Configure the system time zone and date/time.
2. Create a security group and local user account.
3. Collect system information and export Bash history.
4. Combine all tasks into a reusable executable Bash script.

## Key Takeaways

- Bash scripts can automate repetitive system administration tasks.
- Linux provides built-in utilities for managing time, users, groups, and processes.
- Validation commands help verify that configuration changes were applied correctly.
- A reusable baseline script improves consistency when deploying new systems.

## Workflow

### Configure System Time

The system time zone was changed to Pacific/Tahiti and the system clock was manually configured.

**Purpose**

- Configure the correct time zone.
- Set the required system date and time.
- Verify the changes with `timedatectl`.

**Result**

- The system reflected the required time zone and configured date/time.

### Create User Group

A new security group named `CYB300` was created.

**Purpose**

- Create a dedicated local group.
- Prepare the system for assigning user permissions.
- Verify the group exists.

**Result**

- The `CYB300` group was successfully created.

### Create Local User

A new local user was created and assigned to the `CYB300` group.

**Purpose**

- Create a standard user account.
- Assign group membership.
- Configure the required password.

**Result**

- The user account was created and verified using the `id` command.

### Capture Running Processes

Running processes beginning with the letter **n** were exported to a text file.

**Purpose**

- Filter running processes.
- Save command output to a file.
- Verify the exported results.

**Result**

- The `n_processes.txt` file contained the matching processes.

### Export Bash History

The current Bash command history was exported.

**Purpose**

- Preserve executed commands.
- Create an audit trail.
- Verify the exported history file.

**Result**

- A text file containing the Bash history was successfully created.

### Build an Automation Script

All configuration commands were combined into a single executable Bash script.

**Purpose**

- Automate the baseline configuration.
- Consolidate all required tasks.
- Create a reusable deployment script.

**Result**

- An executable Bash script containing every required command was created.

## Notes

### Bash Automation

Bash scripts allow multiple administrative commands to be executed automatically in sequence, reducing manual effort and improving consistency.

### Baseline Configuration

```text
New Linux System
        │
        ▼
Configure Time
        │
        ▼
Create Group
        │
        ▼
Create User
        │
        ▼
Collect System Information
        │
        ▼
Export History
        │
        ▼
Executable Baseline Script
```

### Validation Commands

Each task was verified using a validation command before proceeding. Validating each configuration step helps identify errors early and confirms that changes were successfully applied.

## Commands Used

### Configure Time

```bash
sudo timedatectl set-timezone Pacific/Tahiti
sudo timedatectl set-ntp false
sudo timedatectl set-time "2026-03-01 06:00:00"
timedatectl
```

### Create Group

```bash
sudo groupadd CYB300
getent group CYB300
```

### Create User

```bash
sudo useradd -m -G CYB300 Connor-Arnold
echo "Connor-Arnold:Password123" | sudo chpasswd
id Connor-Arnold
```

### Export Running Processes

```bash
ps -e | grep '^.* n' > n_processes.txt
cat n_processes.txt
```

### Export Bash History

```bash
history > CYB_300_History_Connor_Arnold.txt
cat CYB_300_History_Connor_Arnold.txt
```

### Create Executable Script

```bash
nano baseline.sh
chmod +x baseline.sh
cat baseline.sh
```

## Quick Reference

| Item | Purpose |
|------|---------|
| `timedatectl` | Configure and verify system time settings |
| `groupadd` | Create a local group |
| `useradd` | Create a local user account |
| `chpasswd` | Set a user's password non-interactively |
| `id` | Verify user and group membership |
| `ps` | Display running processes |
| `grep` | Filter command output |
| `history` | Display or export Bash command history |
| `chmod +x` | Make a script executable |

## Related Playbook Pages

- [Bash](../Concepts/bash.md)
- [Linux Users and Groups](../Operating-Systems/Linux/linux-users-and-groups.md) *(coming soon)*
- [Linux File Permissions](../Operating-Systems/Linux/linux-file-permissions.md) *(coming soon)*
- [System Time Management](../Operating-Systems/Linux/system-time-management.md) *(coming soon)*
- [Process Management](../Operating-Systems/Linux/process-management.md) *(coming soon)*
