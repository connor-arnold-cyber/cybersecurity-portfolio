# Lab: SSH Key-Based Authentication and Host Key Rotation

## Overview

This lab demonstrated how to configure OpenSSH for secure remote administration using public-key authentication, disable password-based SSH access, and replace existing server host keys with newly generated RSA and ED25519 keys. These controls strengthened authentication, protected the server's cryptographic identity, and reduced reliance on reusable passwords.

## Lab Summary

This lab follows the lifecycle of SSH key-based authentication and host key management:

1. Install and verify the OpenSSH server and client components.
2. Generate a client authentication key pair and copy the public key to the SSH server.
3. Disable password authentication and verify that access requires the authorized private key.
4. Replace the server host keys, update the allowed algorithms, validate the configuration, and restart SSH.

## Key Takeaways

- SSH public-key authentication uses a private key on the client and a corresponding public key stored on the server.
- The private authentication key must remain protected and should never be copied to the server.
- The `authorized_keys` file identifies which public keys may authenticate to a user account.
- Disabling password authentication reduces exposure to password guessing, credential stuffing, and reused-password attacks.
- Client authentication keys and server host keys perform different security functions.
- Server host keys allow clients to recognize and verify the identity of the SSH server.
- RSA and ED25519 provide different cryptographic key types that OpenSSH can use for server identification.
- `sshd -t` validates the SSH configuration before the service is restarted.
- SSH configuration changes do not take effect until the service is restarted or reloaded.

## Workflow

### Install and Verify the OpenSSH Server

The OpenSSH server package was installed on PLABSRV01 and the service status was checked to confirm that SSH was active and listening for connections.

**Purpose**

- Provide secure remote command-line access to the Ubuntu server.
- Confirm that the SSH daemon installed and started successfully.
- Establish a working server before changing authentication settings.

**Result**

- The `ssh.service` unit reported `active (running)`.
- PLABSRV01 accepted an initial password-authenticated SSH connection.

### Install and Test the OpenSSH Client

The OpenSSH client was installed on PLABCLIENT01 and used to connect to PLABSRV01.

**Purpose**

- Provide the client utilities required to create SSH connections.
- Verify network connectivity between the Ubuntu client and server.
- Establish a working connection before configuring key-based authentication.

**Result**

- PLABCLIENT01 successfully connected to PLABSRV01 over SSH.

### Generate the Client Authentication Key

An RSA authentication key pair was generated on PLABCLIENT01 using `ssh-keygen`.

**Purpose**

- Create a private key that remained on the client.
- Create a public key that could be safely shared with the server.
- Prepare the client for authentication without transmitting a password.

**Result**

- The private key was stored as `~/.ssh/id_rsa`.
- The public key was stored as `~/.ssh/id_rsa.pub`.

### Authorize the Client Public Key

The client public key was copied to PLABSRV01 using `ssh-copy-id` and verified within the server's `authorized_keys` file.

**Purpose**

- Associate the client's public key with the server's administrator account.
- Allow the server to validate proof of possession of the corresponding private key.
- Replace repeated password entry with cryptographic authentication.

**Result**

- One public key was added to PLABSRV01.
- PLABCLIENT01 connected to the server without entering the administrator account password.
- The server's `authorized_keys` file contained the RSA public key associated with `administrator@plabclient01`.

### Disable Password Authentication

The SSH server configuration was updated with `PasswordAuthentication no`, and the SSH service was restarted and enabled.

**Purpose**

- Prevent remote users from authenticating with account passwords.
- Require possession of an authorized private key.
- Reduce exposure to password-based attacks.

**Result**

- Key-based access from PLABCLIENT01 remained available.
- An SSH connection from PLABWIN10 without the authorized private key was denied.

### Remove Existing Server Host Keys

The existing SSH host-key files were removed from PLABSRV01 before replacement keys were created.

**Purpose**

- Replace the existing cryptographic identity of the SSH server.
- Demonstrate host-key rotation.
- Prevent continued use of older server keys.

**Result**

- The previous files matching `/etc/ssh/ssh_host*` were removed.

### Generate New Server Host Keys

New 4096-bit RSA and ED25519 host keys were generated on PLABSRV01.

**Purpose**

- Restore the server keys required by the SSH daemon.
- Configure two supported cryptographic key types.
- Provide new public and private host-key pairs for server identification.

**Result**

- A new 4096-bit RSA host key was created.
- A new ED25519 host key was created.
- The private host-key files were stored in `/etc/ssh`.

### Configure the Server Host Keys and Algorithms

The `hardened.conf` SSH configuration drop-in was updated to reference the new host keys and define the permitted host-key algorithms.

**Purpose**

- Direct the SSH daemon to the replacement host-key files.
- Restrict server identification to the configured ED25519 and RSA SHA-2 algorithms.
- Centralize the hardened settings in a dedicated configuration file.

**Result**

- The configuration referenced both replacement host keys.
- The permitted host-key algorithm list was successfully added.

### Validate and Apply the SSH Configuration

The SSH configuration was tested with `sshd -t` before the service was restarted and enabled.

**Purpose**

- Detect syntax or configuration errors before applying the changes.
- Avoid restarting SSH with an invalid configuration.
- Confirm that the service remained available after the host-key rotation.

**Result**

- `sshd -t` returned no errors.
- The SSH service restarted successfully.
- The service reported `active (running)` with the replacement keys installed.

## Notes

### Lab Environment

| Device | Operating System | Role |
|--------|------------------|------|
| PLABSRV01 | Ubuntu 20.04 | OpenSSH server |
| PLABCLIENT01 | Ubuntu 20.04 Desktop | Authorized SSH client |
| PLABWIN10 | Windows 10 | Initial administration and unauthorized-client test |

### Authentication Keys and Host Keys

The lab used two separate types of SSH key pairs.

**Client authentication keys**

- Generated on PLABCLIENT01.
- The private key remained on the client.
- The public key was copied to the server's `authorized_keys` file.
- Used to prove that the connecting client possessed the authorized private key.

**Server host keys**

- Generated and stored on PLABSRV01.
- Used by the SSH server to prove its identity to connecting clients.
- Replacing these keys changes the server fingerprint seen by clients.

A client authentication key authorizes a user, while a server host key identifies the server.

### SSH Public-Key Authentication Flow

```text
PLABCLIENT01
├── Private key: ~/.ssh/id_rsa
└── Public key:  ~/.ssh/id_rsa.pub
          │
          │ ssh-copy-id
          ▼
PLABSRV01
└── ~/.ssh/authorized_keys
          │
          │ Client proves possession of private key
          ▼
SSH authentication succeeds
```

### Lab Terminology

The lab described the first exercise as certificate-based authentication. The implemented commands configured standard SSH public-key authentication through `ssh-keygen`, `ssh-copy-id`, and `authorized_keys`. No SSH Certificate Authority was created, and the client key was not signed as an SSH certificate.

### Configuration Drop-In Directory

The `/etc/ssh/sshd_config.d` directory was not present in the fresh server environment. It was created before the `hardened.conf` drop-in file was added.

### Host-Key Rotation Precaution

Existing host keys should not be removed unless replacement keys can be generated immediately through an active console or another recovery method. Restarting the SSH service without valid host keys could make the server unavailable for remote administration.

## Commands Used

### Connect to the SSH Server From Windows

```powershell
cls
ssh administrator@192.168.0.1
```

### Install and Verify the OpenSSH Server

```bash
sudo apt update
sudo apt install ssh
sudo systemctl status ssh
clear
```

### Install and Test the OpenSSH Client

```bash
sudo apt update
sudo apt install openssh-client
ssh administrator@192.168.0.1
exit
clear
```

### Generate and Inspect the Client Authentication Key

```bash
ssh-keygen
cd .ssh
ls
```

### Copy and Test the Client Public Key

```bash
ssh-copy-id administrator@192.168.0.1
ssh administrator@192.168.0.1
```

### Inspect the Authorized Public Key

```bash
cd .ssh
less authorized_keys
```

### Disable Password Authentication

```bash
sudoedit /etc/ssh/sshd_config.d/hardened.conf
sudo systemctl restart --now ssh.service
sudo systemctl enable --now ssh.service
```

The following configuration was added:

```text
PasswordAuthentication no
```

### Test Access Without the Authorized Key

```powershell
ssh administrator@192.168.0.1
```

### Remove and Replace the Server Host Keys

```bash
sudo rm /etc/ssh/ssh_host*
sudo ssh-keygen -q -N "" -t rsa -b 4096 -f /etc/ssh/ssh_host_rsa_key
sudo ssh-keygen -q -N "" -t ed25519 -f /etc/ssh/ssh_host_ed25519_key
```

### Create the SSH Configuration Drop-In

```bash
sudo mkdir -p /etc/ssh/sshd_config.d
sudo nano /etc/ssh/sshd_config.d/hardened.conf
```

The following configuration was added:

```text
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
HostKeyAlgorithms ssh-ed25519,ssh-ed25519-cert-v01@openssh.com,sk-ssh-ed25519@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com,rsa-sha2-256,rsa-sha2-512,rsa-sha2-256-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com
```

### Validate and Apply the Final Configuration

```bash
sudo cat /etc/ssh/sshd_config.d/hardened.conf
sudo sshd -t
sudo systemctl restart --now ssh.service
sudo systemctl enable --now ssh.service
```

### Verify the Replacement Keys and SSH Service

```bash
sudo grep -E '^(HostKey|HostKeyAlgorithms)' /etc/ssh/sshd_config.d/hardened.conf
sudo ls -l /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_ed25519_key
sudo systemctl status ssh --no-pager
```

## Quick Reference

| Item | Purpose |
|------|---------|
| SSH | Provides encrypted remote administration |
| OpenSSH Server | Accepts and manages incoming SSH connections |
| OpenSSH Client | Initiates SSH connections and manages client keys |
| `ssh-keygen` | Generates SSH public and private key pairs |
| `ssh-copy-id` | Copies a client public key to a remote account |
| `id_rsa` | Client RSA private authentication key |
| `id_rsa.pub` | Client RSA public authentication key |
| `authorized_keys` | Lists public keys authorized to access an account |
| SSH host key | Identifies the SSH server to connecting clients |
| `PasswordAuthentication no` | Disables password-based SSH authentication |
| `HostKey` | Specifies a private host-key file used by `sshd` |
| `HostKeyAlgorithms` | Defines the permitted server host-key algorithms |
| `sshd -t` | Tests the SSH server configuration for errors |
| `systemctl restart` | Restarts the SSH service to apply changes |
| TCP port 22 | Default network port used by SSH |

## Related Playbook Pages

- [SSH (Secure Shell)](../concepts/ssh-secure-shell.md) (coming soon)
- [Authentication](../concepts/authentication.md)
- [Key Management](../concepts/key-management.md)
- [Public and Private Key Encryption](../concepts/public-&-private-key-encryption.md)
- [Ports and Port Numbers](../concepts/ports-and-port-numbers.md)
- [OpenSSH](../tools/openssh.md) (coming soon)
- [Asymmetric Encryption](../../data-security/concepts/asymmetric-encryption.md)
- [RSA](../../data-security/concepts/rsa.md)
- [Elliptic Curve Cryptography (ECC)](../../data-security/concepts/ecc-elliptic-curve-cryptography.md)
