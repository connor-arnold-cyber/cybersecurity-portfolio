# Security-Enhanced Linux (SELinux)

## Overview

(Security-Enhanced Linux overview...)

---

## Why SELinux Exists

Traditional Linux permissions use Discretionary Access Control (DAC).

SELinux adds Mandatory Access Control (MAC), allowing the operating system to enforce security policies even if normal file permissions would otherwise allow access.

Example:

- User owns a file.
- File permissions allow reading.
- SELinux policy still blocks access.

---

## Key Concepts

- Mandatory Access Control (MAC)
- Security contexts (labels)
- Policies
- Types
- Domains
- Least privilege
- Process isolation

---

## Operating Modes

| Mode | Description |
|------|-------------|
| Enforcing | Policies are enforced. Unauthorized actions are blocked. |
| Permissive | Violations are logged but not blocked. |
| Disabled | SELinux is turned off. |

---

# Checking SELinux

## Check overall status

```bash
sestatus
```

Displays:

- Enabled/disabled
- Current mode
- Config file mode
- Loaded policy

---

## Quick mode check

```bash
getenforce
```

Returns:

- Enforcing
- Permissive
- Disabled

---

## Switch modes (temporary)

Enable enforcing:

```bash
sudo setenforce 1
```

Enable permissive:

```bash
sudo setenforce 0
```

Changes last until reboot.

---

# Viewing Security Contexts

View file labels:

```bash
ls -Z
```

Long format:

```bash
ls -lZ
```

View directory labels recursively:

```bash
ls -RZ
```

---

View process labels:

```bash
ps auxZ
```

Shows which SELinux domain each process is running under.

---

# Managing Contexts

Temporarily change a context:

```bash
sudo chcon -t TYPE file
```

Common options:

- `-t` → Change type
- `-u` → Change SELinux user
- `-r` → Change role
- `-Rv` → Recursive + verbose

Example:

```bash
sudo chcon -Rv -t httpd_sys_content_t /website
```

---

Restore default context:

```bash
sudo restorecon file
```

Recursive:

```bash
sudo restorecon -Rv directory
```

---

# Managing Policies

List booleans:

```bash
getsebool -a
```

View one boolean:

```bash
getsebool httpd_enable_homedirs
```

Enable permanently:

```bash
sudo setsebool -P httpd_enable_homedirs on
```

Disable:

```bash
sudo setsebool -P httpd_enable_homedirs off
```

---

# Managing Ports

List all managed ports:

```bash
sudo semanage port -l
```

Search ports:

```bash
sudo semanage port -l | grep http
```

Add a port:

```bash
sudo semanage port -a -t http_port_t -p tcp 50080
```

Delete a port:

```bash
sudo semanage port -d -t http_port_t -p tcp 50080
```

Modify a port:

```bash
sudo semanage port -m -t http_port_t -p tcp 8080
```

---

# Troubleshooting

View recent AVC denials:

```bash
ausearch -m avc
```

Generate policy suggestions:

```bash
audit2allow
```

---

# Common Workflow

1. Check SELinux status.
2. Confirm current mode.
3. Examine labels.
4. Review denial logs.
5. Correct labels or policies.
6. Test again.

---

# Best Practices

- Leave SELinux in Enforcing mode.
- Prefer restorecon over chcon for permanent fixes.
- Avoid disabling SELinux.
- Use least privilege.
- Keep labels consistent.

---

# Memorize

Commands:

- sestatus
- getenforce
- setenforce
- ls -Z
- ps auxZ
- restorecon
- chcon
- semanage
- getsebool
- setsebool

Concepts:

- MAC
- Security Context
- Type
- Domain
- Policy
- AVC Denial

---

# Related Concepts

- Linux Permissions (DAC)
- AppArmor
- Linux Hardening
- Principle of Least Privilege
- Access Control

---

# Related Labs & Projects

- CYB 300 Module 1 – Securing Linux Devices Lab
