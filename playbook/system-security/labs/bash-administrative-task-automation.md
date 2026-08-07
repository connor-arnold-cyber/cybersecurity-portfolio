# Lab: Bash Administrative Task Automation

CYB 300 Module Six Activity - Scripting Administrative Tasks

## Overview

This lab demonstrated how Bourne Again Shell (Bash) scripting can automate repetitive Linux administrative and security tasks involving account provisioning, backups, network connectivity testing, group management, account auditing, and process inventory. Variables, repetition structures, and compound conditional statements were incorporated to make administrative operations repeatable, controlled, and verifiable.

## Lab Summary

This lab follows the lifecycle of administrative task automation with Bash:

1. Human Resources, Finance, and Sales groups were defined and twelve employee accounts were provisioned through a reusable script.
2. The `/home` directory was compressed and backed up to `/backup`.
3. Internet Protocol (IP) addresses ending in odd numbers were evaluated with the Ping utility and results were written to `ping.txt`.
4. An Audit group workflow collected employees assigned to Human Resources and Finance.
5. User accounts were evaluated for inactive or disabled status and matching accounts were written to `inactive_users.txt`.
6. Running processes were collected with `ps aux` and written to `running_processes.txt`.

## Key Takeaways

- Bash scripts can reduce the effort required for repetitive administrative tasks.
- Variables make scripts easier to reuse and maintain.
- Repetition structures allow the same operation to be applied across multiple users, groups, files, or network addresses.
- Compound conditional statements allow multiple conditions to be evaluated before an action occurs.
- Administrative scripts remain subject to Linux permissions and may require `sudo`.
- Compressed archives provide an efficient method for backing up directories.
- Ping can be incorporated into scripts to automate network connectivity testing.
- User and group management can be standardized through scripted provisioning.
- Account and process inventories can be redirected to files for later review.

## Workflow

### User and Group Provisioning

A Bash workflow was designed to create Human Resources, Finance, and Sales groups and provision twelve employee accounts. Linux-safe group names were used for the reference implementation, and each employee was assigned to one organizational group.

**Purpose**

- Automate repetitive user provisioning.
- Standardize organizational group membership.
- Apply a consistent initial password.
- Reduce manual account-management work.

**Result**

- A complete reference implementation was created for provisioning three groups and twelve accounts.
- This workflow was not executed during the submitted lab session.

### Home Directory Backup

A Bash script created the `/backup` directory and compressed `/home` into `/backup/home_backup.tar.gz`. The archive was then inspected to verify that it existed and contained files.

**Purpose**

- Preserve user data in a compressed archive.
- Automate a common system administration task.
- Verify that the resulting backup contained data.

**Result**

- `/backup/home_backup.tar.gz` was successfully created.
- The archive contents were successfully displayed for verification.

### Odd-Numbered Internet Protocol Address Connectivity Test

A Bash workflow was designed to identify Internet Protocol addresses ending in odd numbers, test them with Ping, and record connectivity results in `ping.txt`.

**Purpose**

- Automate repetitive network connectivity testing.
- Demonstrate iteration across multiple network addresses.
- Preserve connectivity results for later review.

**Result**

- A complete reference implementation was created for generating `ping.txt`.
- This workflow was not executed during the submitted lab session.

### Audit Group Configuration

A Bash workflow was designed to create an Audit group and add employee accounts whose primary groups were Human Resources or Finance.

**Purpose**

- Consolidate selected employee accounts into an auditing group.
- Automate repetitive group-membership changes.
- Demonstrate scripted access and membership management.

**Result**

- A complete reference implementation was created for Audit group population.
- This workflow was not executed during the submitted lab session.

### Inactive and Disabled Account Inventory

A Bash workflow was designed to inspect normal user accounts for locked status or extended inactivity and write matching usernames to `inactive_users.txt`.

**Purpose**

- Identify accounts that may require administrative review.
- Automate account-status auditing.
- Produce a persistent report for later analysis.

**Result**

- A complete reference implementation was created for generating `inactive_users.txt`.
- This workflow was not executed during the submitted lab session.

### Running Process Inventory

A Bash script used `ps aux` to capture the system's running processes and redirect them to `running_processes.txt`. The output file was then displayed to verify that process information had been collected.

**Purpose**

- Create an inventory of active processes.
- Automate basic system monitoring.
- Preserve process information for later review.

**Result**

- `running_processes.txt` was successfully created.
- The file contained the system's running process list.

## Notes

### Required Bash Structures

Each script design incorporated the three programming structures required by the activity:

```text
Variable declaration
        |
        v
Repetition structure
        |
        v
Compound conditional
        |
        v
Administrative action
        |
        v
Verification or output
```

Variables stored reusable values such as filenames, directories, groups, and thresholds. Repetition structures applied actions across multiple objects, while compound conditional statements evaluated multiple requirements before allowing an action to continue.

### Privilege Requirements

Bash scripts did not bypass Linux access controls. Operations involving user accounts, groups, passwords, and protected directories required elevated privileges through `sudo`.

### Reference Implementation Scope

The assignment required only two of the six administrative tasks to be selected for submission. The running-process and home-directory backup scripts were executed and verified during the lab. The remaining four scripts below document complete reference implementations for the other scenario tasks and were not executed.

### Linux Group Naming

The scenario refers to Human Resources, Finance, and Sales. The reference scripts use `human_resources`, `finance`, and `sales` because Linux group identifiers are represented as single names without spaces.

### Ping Network Assumption

The assignment does not specify the exact subnet to scan. The reference Ping script derives the first three octets from the Xubuntu system's primary Internet Protocol address and treats the local network as a `/24` network. The prefix should be changed if the target environment uses a different subnet.

### Inactive Account Definition

The scenario does not define a specific inactivity period. The reference implementation uses 90 days as an administrative threshold and also identifies password-locked accounts. The threshold can be changed through the `INACTIVE_DAYS` variable.

### Script One Troubleshooting

The running-process script initially used inconsistent capitalization for the `OUTPUT_FILE` variable. Because Bash variable names are case-sensitive, the script attempted to redirect output using an undefined variable.

The declaration was corrected to:

```bash
OUTPUT_FILE="running_processes.txt"
```

The script then executed successfully.

## Commands Used

### Running Process Inventory

```bash
nano script1.txt
bash script1.txt
head running_processes.txt
echo "Connor Arnold"
cat script1.txt
```

The executed script was:

```bash
#!/bin/bash

# Name: Connor Arnold
# Date: August 7, 2026
# Course: CYB 300 System and Communication Security

# Variable declaration and usage
OUTPUT_FILE="running_processes.txt"

# Repetition structure
for attempt in 1 2 3
do
    ps aux > "$OUTPUT_FILE"

    # Compound conditional statement
    if [[ -f "$OUTPUT_FILE" && -s "$OUTPUT_FILE" ]]
    then
        echo "Running processes successfully saved to $OUTPUT_FILE"
        break
    fi
done
```

### Home Directory Backup

```bash
nano script2.txt
sudo bash script2.txt
sudo ls -lh /backup
sudo tar -tzf /backup/home_backup.tar.gz | head
echo "Connor Arnold"
cat script2.txt
```

The executed script was:

```bash
#!/bin/bash

# Name: Connor Arnold
# Date: August 7, 2026
# Course: CYB 300 System and Communication Security

# Variable declaration and usage
BACKUP_DIR="/backup"
BACKUP_FILE="$BACKUP_DIR/home_backup.tar.gz"

mkdir -p "$BACKUP_DIR"

# Repetition structure
for attempt in 1 2 3
do
    tar -czf "$BACKUP_FILE" /home

    # Compound conditional statement
    if [[ -f "$BACKUP_FILE" && -s "$BACKUP_FILE" ]]
    then
        echo "Home directory successfully backed up to $BACKUP_FILE"
        break
    fi
done
```

### User and Group Provisioning — Reference Implementation, Not Executed

Example usernames were used because the assignment scenario specifies twelve accounts but does not provide employee names.

```bash
#!/bin/bash

# Name: Connor Arnold
# Date: August 7, 2026
# Course: CYB 300 System and Communication Security

# Variable declaration and usage
PASSWORD='NewP@$$w0rd'

GROUPS=(
    "human_resources"
    "finance"
    "sales"
)

USERS=(
    "hr01:human_resources"
    "hr02:human_resources"
    "hr03:human_resources"
    "hr04:human_resources"
    "fin01:finance"
    "fin02:finance"
    "fin03:finance"
    "fin04:finance"
    "sales01:sales"
    "sales02:sales"
    "sales03:sales"
    "sales04:sales"
)

# Repetition structure
for group in "${GROUPS[@]}"
do
    groupadd -f "$group"
done

for entry in "${USERS[@]}"
do
    USERNAME="${entry%%:*}"
    USERGROUP="${entry##*:}"

    # Compound conditional statement
    if [[ -n "$USERNAME" && -n "$USERGROUP" ]]
    then
        if ! id "$USERNAME" &>/dev/null
        then
            useradd -m -g "$USERGROUP" "$USERNAME"
        fi

        echo "$USERNAME:$PASSWORD" | chpasswd
    fi
done

echo "User and group provisioning complete."
```

### Odd-Numbered Internet Protocol Address Ping Test — Reference Implementation, Not Executed

```bash
#!/bin/bash

# Name: Connor Arnold
# Date: August 7, 2026
# Course: CYB 300 System and Communication Security

# Variable declaration and usage
OUTPUT_FILE="ping.txt"
LOCAL_IP=$(hostname -I | awk '{print $1}')
NETWORK_PREFIX=$(echo "$LOCAL_IP" | cut -d. -f1-3)

> "$OUTPUT_FILE"

# Repetition structure
for HOST in $(seq 1 2 253)
do
    IP_ADDRESS="$NETWORK_PREFIX.$HOST"

    # Compound conditional statement
    if [[ "$HOST" -ge 1 && "$HOST" -le 253 ]]
    then
        if ping -c 1 -W 1 "$IP_ADDRESS" > /dev/null 2>&1
        then
            echo "$IP_ADDRESS - reachable" >> "$OUTPUT_FILE"
        else
            echo "$IP_ADDRESS - unreachable" >> "$OUTPUT_FILE"
        fi
    fi
done

echo "Ping results saved to $OUTPUT_FILE"
```

### Audit Group Configuration — Reference Implementation, Not Executed

```bash
#!/bin/bash

# Name: Connor Arnold
# Date: August 7, 2026
# Course: CYB 300 System and Communication Security

# Variable declaration and usage
AUDIT_GROUP="audit"
SOURCE_GROUPS=("human_resources" "finance")

groupadd -f "$AUDIT_GROUP"

# Repetition structure
for SOURCE_GROUP in "${SOURCE_GROUPS[@]}"
do
    GROUP_ID=$(getent group "$SOURCE_GROUP" | cut -d: -f3)

    # Compound conditional statement
    if [[ -n "$GROUP_ID" && "$GROUP_ID" =~ ^[0-9]+$ ]]
    then
        while IFS=: read -r USERNAME PASSWORD USER_ID USER_GROUP_ID GECOS HOME SHELL
        do
            if [[ "$USER_GROUP_ID" == "$GROUP_ID" && "$USER_ID" -ge 1000 ]]
            then
                usermod -aG "$AUDIT_GROUP" "$USERNAME"
            fi
        done < /etc/passwd
    fi
done

echo "Audit group configuration complete."
```

### Inactive and Disabled Account Inventory — Reference Implementation, Not Executed

```bash
#!/bin/bash

# Name: Connor Arnold
# Date: August 7, 2026
# Course: CYB 300 System and Communication Security

# Variable declaration and usage
OUTPUT_FILE="inactive_users.txt"
INACTIVE_DAYS=90

> "$OUTPUT_FILE"

INACTIVE_USERS=$(lastlog -b "$INACTIVE_DAYS" | awk 'NR > 1 {print $1}')

# Repetition structure
while IFS=: read -r USERNAME PASSWORD USER_ID USER_GROUP_ID GECOS HOME SHELL
do
    if [[ "$USER_ID" -ge 1000 && "$USERNAME" != "nobody" ]]
    then
        ACCOUNT_STATUS=$(passwd -S "$USERNAME" 2>/dev/null | awk '{print $2}')
        IS_INACTIVE="false"

        if grep -qx "$USERNAME" <<< "$INACTIVE_USERS"
        then
            IS_INACTIVE="true"
        fi

        # Compound conditional statement
        if [[ "$ACCOUNT_STATUS" == "L" || "$IS_INACTIVE" == "true" ]]
        then
            echo "$USERNAME" >> "$OUTPUT_FILE"
        fi
    fi
done < /etc/passwd

echo "Inactive and disabled accounts saved to $OUTPUT_FILE"
```

## Quick Reference

| Item | Purpose |
|------|---------|
| Bash | Automates Linux administrative tasks |
| Variable | Stores reusable values within a script |
| `for` | Repeats commands across a defined set of values |
| `while` | Repeats commands while processing input |
| `[[ ... ]]` | Evaluates conditional expressions |
| `&&` | Requires both conditions to evaluate as true |
| `||` | Allows either condition to evaluate as true |
| `groupadd` | Creates Linux groups |
| `useradd` | Creates Linux user accounts |
| `usermod -aG` | Adds an existing user to a supplementary group |
| `chpasswd` | Updates account passwords from standard input |
| `getent` | Retrieves entries from system account databases |
| `ps aux` | Lists running processes |
| `tar -czf` | Creates a gzip-compressed tar archive |
| `ping` | Tests Internet Protocol connectivity |
| `lastlog` | Displays user login history |
| `passwd -S` | Displays account password status |
| `sudo` | Executes permitted commands with elevated privileges |
| `running_processes.txt` | Stores the running process inventory |
| `ping.txt` | Stores Ping connectivity results |
| `inactive_users.txt` | Stores inactive or disabled usernames |
| `/backup/home_backup.tar.gz` | Stores the compressed `/home` backup |

## Related Playbook Pages

- [Bash Cheat Sheet](../tools/bash-cheat-sheet.md)
- [Bash Scripting Guide](../tools/bash-scripting-guide.md)
- [Common Linux Flags](../tools/common-linux-flags.md)
- [Terminal Command Equivalents](../tools/terminal-command-equivalents.md)
- [Ping](../../connection-security/tools/ping.md)
