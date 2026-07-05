# Security-Enhanced Linux (SELinux)

## Overview

Security-Enhanced Linux (SELinux) is a Mandatory Access Control (MAC) security framework built into many Linux distributions, including Red Hat Enterprise Linux, AlmaLinux, Rocky Linux, and CentOS.

Unlike traditional Linux permissions, SELinux restricts what applications, users, and processes are allowed to access—even if normal file permissions would allow it.

## Key Concepts

- Mandatory Access Control (MAC)
- Security contexts (labels)
- Least privilege
- Policy enforcement
- Process isolation

## Operating Modes

### Enforcing

SELinux actively enforces security policies and blocks unauthorized actions.

### Permissive

SELinux allows actions but logs policy violations for troubleshooting.

### Disabled

SELinux is completely disabled.

## Security Contexts

SELinux assigns every file, directory, process, and port a security context (label).

Example:

```
httpd_sys_content_t
```

Apache can only access files with the correct context.

Contexts can be viewed using:

```bash
ls -lZ
```

## Common Commands

### Check SELinux status

```bash
sestatus
```

Displays:

- Whether SELinux is enabled
- Current mode
- Configuration mode
- Loaded policy

---

### Show current mode

```bash
getenforce
```

Possible output:

- Enforcing
- Permissive
- Disabled

---

### Temporarily enable enforcing mode

```bash
sudo setenforce 1
```

---

### Temporarily enable permissive mode

```bash
sudo setenforce 0
```

or

```bash
sudo setenforce permissive
```

Changes last until the next reboot.

---

### View security contexts

```bash
ls -lZ
```

Lists SELinux labels for files and directories.

---

### View process contexts

```bash
ps auxZ
```

Displays SELinux labels for running processes.

---

### Change a security context

```bash
sudo chcon -Rv --type=httpd_sys_content_t /website
```

Changes the context label so Apache can access the directory.

---

### View allowed ports

```bash
sudo semanage port -l
```

---

### Show only HTTP ports

```bash
sudo semanage port -l | grep http
```

---

### Add a new allowed HTTP port

```bash
sudo semanage port -a -t http_port_t -p tcp 50080
```

Allows Apache to use TCP port 50080.

## Common Workflow

1. Check SELinux status.
2. Verify current mode.
3. Examine security contexts.
4. Modify contexts if necessary.
5. Configure policies or ports.
6. Test the application.

## Best Practices

- Leave SELinux in Enforcing mode whenever possible.
- Use Permissive mode only for troubleshooting.
- Avoid disabling SELinux.
- Keep contexts properly labeled.
- Follow the principle of least privilege.

## Related Labs & Projects

- Securing Linux Devices Lab
- Apache Web Server Hardening
- Linux Server Administration
