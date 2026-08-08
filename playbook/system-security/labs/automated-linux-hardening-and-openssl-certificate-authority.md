# Lab: Automated Linux Hardening and OpenSSL Certificate Authority

CYB-300 Final Project

## Overview

This lab demonstrated how automated Bash scripting, operating system security baselines, and Public Key Infrastructure (PKI) could be combined to secure systems at a new organizational location. A single executable script applied Linux configuration requirements for hostname management, time-zone configuration, process collection, screen locking, and security-log collection, while OpenSSL was used to create and verify an encrypted root Certificate Authority (CA) that met defined cryptographic requirements.

## Lab Summary

This lab follows the lifecycle of automated Linux baseline hardening and Public Key Infrastructure deployment:

1. A Bash script was created to apply the required operating system baseline settings.
2. The script was made executable, run, corrected where necessary, and each resulting configuration was verified.
3. System process data and the final 50 `/var/log/syslog` entries were collected into dedicated text files.
4. An encrypted 4096-bit root Certificate Authority private key and one-year self-signed certificate were created with OpenSSL.
5. Certificate settings were verified and the Certificate Signing Request (CSR), trust, and certificate-management workflow was evaluated.
6. The implemented settings were translated into an operating system security-configuration checklist for repeatable deployment and verification.

## Key Takeaways

- Bash scripts can apply repeatable security configurations across multiple Linux systems.
- Automated configuration reduces inconsistent settings and manual administrative errors.
- `hostnamectl` and `timedatectl` provide centralized management of system identity and time-zone settings.
- `ps aux` can capture a complete snapshot of active processes for review or documentation.
- Xfce screensaver settings can be managed through `xfconf-query`.
- System logs can be filtered and redirected into files for security review and evidence collection.
- A root Certificate Authority private key must be strongly protected because it anchors trust for certificates issued beneath it.
- OpenSSL can generate encrypted private keys, self-signed certificates, and certificate-verification output from the command line.
- Certificate Signing Requests allow systems to request trusted certificates without exposing their private keys.
- Security checklists complement automation by documenting the required baseline and how each setting should be verified.

## Workflow

### Create the Automated Hardening Script

A single Bash script was created to apply the required baseline configuration. The script changed the computer name and time zone, captured running processes, configured the Xfce screensaver and lock settings, and exported the final 50 system log entries.

**Purpose**

- Apply multiple configuration requirements through one repeatable process.
- Reduce manual configuration differences between systems.
- Create a reusable baseline that could be reviewed and modified as organizational requirements changed.

**Result**

- The completed script contained all required hardening commands and was given executable permissions.

### Configure the System Identity and Time Zone

The script attempted to rename the system according to the required naming convention and changed the system time zone to `America/Denver`.

**Purpose**

- Establish a predictable naming convention for managed systems.
- Ensure the system used the correct local time zone for the Colorado location.
- Improve consistency when reviewing logs, system records, and administrative information.

**Result**

- The system reported `America/Denver` as its configured time zone.
- The requested underscore in `C_Arnold` was not accepted as a standard Linux static hostname, and the resulting hostname was displayed as `CArnold`.

### Capture Running Processes

The `ps aux` command was redirected to `running_processes.txt` to record the processes that were active when the script executed.

**Purpose**

- Provide a snapshot of active system processes.
- Create a file that could be reviewed for unexpected or unauthorized activity.
- Demonstrate how command output could be collected automatically for later analysis.

**Result**

- `running_processes.txt` was created and contained the expected process table and active processes.

### Configure the Three-Minute Screen Lock

Xfce screensaver properties were configured through `xfconf-query`. Idle activation was enabled, the idle delay was set to three minutes, screen locking was enabled, and locking was configured to occur when the screensaver activated.

**Purpose**

- Reduce the risk of unauthorized access to an unattended workstation.
- Apply the screen-lock requirement through the automated baseline rather than manual graphical configuration.
- Make the setting directly verifiable from the command line.

**Result**

- Idle activation returned `true`.
- The idle delay returned `3`.
- Screen locking returned `true`.
- Locking on screensaver activation returned `true`.

### Collect Security Log Entries

The final 50 entries from `/var/log/syslog` were redirected into `SecurityLog_Arnold.txt`.

**Purpose**

- Preserve a small set of recent system events for security review.
- Demonstrate automatic collection of log information as part of a hardening process.
- Create an easily verified output file without modifying the original system log.

**Result**

- `SecurityLog_Arnold.txt` contained exactly 50 lines of system log data.

### Create the Colorado Office Root Certificate Authority

OpenSSL was used to generate a 4096-bit Rivest-Shamir-Adleman (RSA) private key protected with Advanced Encryption Standard 256-bit (AES-256) encryption. A self-signed root Certificate Authority certificate was then created using Secure Hash Algorithm 256 (SHA-256), a one-year validity period, and the required Colorado organization information.

**Purpose**

- Establish a root of trust for certificate-based authentication and secure communications.
- Protect the root Certificate Authority private key with strong encryption.
- Apply the organization's required cryptographic settings.

**Result**

- The resulting certificate identified `Colorado Office Root` as the common name.
- The certificate contained the required United States and Colorado subject information.
- Verification showed a 4096-bit public key and `sha256WithRSAEncryption`.
- The certificate validity period was one year.

### Verify the Certificate Authority

OpenSSL inspection commands were used to display the certificate subject, validity dates, public-key size, and signature algorithm.

**Purpose**

- Confirm that the generated certificate matched the required configuration.
- Detect incorrect certificate properties before the Certificate Authority was used to issue certificates.
- Provide command-line evidence of the cryptographic settings.

**Result**

- The subject, dates, 4096-bit key size, and Secure Hash Algorithm 256 signature were successfully confirmed.

### Evaluate the Certificate Signing Request Process

The intended certificate-enrollment workflow was evaluated for systems at the new location. Each server or workstation would generate its own public and private key pair and submit a Certificate Signing Request containing its public key and identity information to the Certificate Authority.

**Purpose**

- Keep the requesting system's private key under its own control.
- Allow the Certificate Authority to verify the request before establishing trust.
- Provide a controlled process for issuing certificates to approved organizational systems.

**Result**

- The expected workflow required identity verification, Certificate Authority approval, certificate signing, installation, expiration management, and revocation when trust was no longer appropriate.

### Translate the Configuration Into a Security Checklist

The hardening requirements implemented by the Bash script were converted into a checklist describing the required configuration and a verification method for each setting.

**Purpose**

- Document the approved operating system baseline independently of the automation script.
- Give administrators and auditors a consistent method for verifying system configuration.
- Make future changes to the baseline easier to track and review.

**Result**

- The final checklist covered computer naming, Denver time-zone configuration, process collection, the three-minute screen lock, security-log collection, and executable-script verification.

## Notes

### Linux Hostname Limitation

The required naming format used an underscore in `C_Arnold`. The `hostnamectl` command accepted the requested value but normalized the resulting static hostname to `CArnold`. A later attempt to apply the underscore directly with the `hostname` command returned an invalid-hostname error.

Standard Linux hostnames have more restrictive character requirements than arbitrary display names. When developing a real organizational baseline, the organization's naming convention should therefore be designed around the hostname rules enforced by the target operating system.

### Xfce Screen-Lock Configuration

The Xfce configuration was controlled through the `xfce4-screensaver` channel using `xfconf-query`.

The important properties used in the completed configuration were:

```text
/saver/idle-activation/enabled = true
/saver/idle-activation/delay = 3
/lock/enabled = true
/lock/saver-activation/enabled = true
/lock/saver-activation/delay = 0
```

The three-minute idle delay controlled when the screensaver activated. The zero-minute saver-activation lock delay caused the workstation to lock immediately once the screensaver became active.

### Script Troubleshooting

The first execution of the script failed on the Xfce configuration lines because `xfconf-query` had been entered as `xconf-query`.

The installed package was checked and `xfconf-query 4.16.0` was confirmed to be present. The script was reopened, the command name was corrected on each affected line, and the unnecessary attempt to start another `xfce4-screensaver` process was removed because the screensaver was already active in the session.

This demonstrated the importance of reading exact shell errors before changing packages or system configuration.

### Certificate Signing Request Workflow

A Certificate Signing Request allowed a server or workstation to request a certificate while retaining control of its private key.

```text
Server or Workstation
        |
        v
Generate Public/Private Key Pair
        |
        v
Create Certificate Signing Request
        |
        v
Submit Request to Certificate Authority
        |
        v
Verify Identity and Authorization
        |
        v
Certificate Authority Signs Certificate
        |
        v
Install Issued Certificate
        |
        v
Manage Expiration and Revocation
```

The Certificate Authority signed the requesting system's public key and identity information rather than receiving the private key. This preserved private-key confidentiality while allowing other systems that trusted the root Certificate Authority to validate the issued certificate.

### Hardening Baselines and Checklists

The Bash script and security checklist served different but complementary purposes. The script automated implementation, while the checklist documented what the final system state should be and how each control could be verified.

This distinction is important in larger environments because an automation process can fail, be changed, or be run against an unexpected system. Independent verification against a documented baseline provides an additional control.

## Commands Used

### Initial Environment Verification

```bash
echo "Connor Arnold"
hostname
timedatectl
xfconf-query -c xfce4-screensaver -l
ls -l /var/log/syslog
command -v xfce4-screensaver
pgrep -a xfce4-screensaver
xfconf-query --version
```

### Create and Review the Hardening Script

```bash
nano cyb300_hardening.sh
chmod +x cyb300_hardening.sh
ls -l cyb300_hardening.sh
cat -n cyb300_hardening.sh
```

The final script contained:

```bash
#!/bin/bash

sudo hostnamectl set-hostname C_Arnold
sudo timedatectl set-timezone America/Denver
ps aux > running_processes.txt

xfconf-query -c xfce4-screensaver -p /saver/enabled -n -t bool -s true
xfconf-query -c xfce4-screensaver -p /saver/idle-activation/enabled -n -t bool -s true
xfconf-query -c xfce4-screensaver -p /saver/idle-activation/delay -n -t int -s 3
xfconf-query -c xfce4-screensaver -p /lock/enabled -n -t bool -s true
xfconf-query -c xfce4-screensaver -p /lock/saver-activation/enabled -n -t bool -s true
xfconf-query -c xfce4-screensaver -p /lock/saver-activation/delay -n -t int -s 0

sudo tail -n 50 /var/log/syslog > SecurityLog_Arnold.txt
```

### Execute the Hardening Script

```bash
./cyb300_hardening.sh
```

### Verify the Hostname and Time Zone

```bash
hostname
timedatectl
sudo hostname C_Arnold
hostname
```

### Verify the Running Process File

```bash
ls -l running_processes.txt
head running_processes.txt
```

### Verify the Screen-Lock Configuration

```bash
xfconf-query -c xfce4-screensaver -p /saver/idle-activation/enabled
xfconf-query -c xfce4-screensaver -p /saver/idle-activation/delay
xfconf-query -c xfce4-screensaver -p /lock/enabled
xfconf-query -c xfce4-screensaver -p /lock/saver-activation/enabled
```

### Verify the Security Log File

```bash
ls -l SecurityLog_Arnold.txt
wc -l SecurityLog_Arnold.txt
tail SecurityLog_Arnold.txt
```

### Create the Root Certificate Authority

```bash
openssl genrsa -aes256 -out ColoradoOfficeRoot.key 4096
openssl req -x509 -new -key ColoradoOfficeRoot.key -sha256 -days 365 -out ColoradoOfficeRoot.crt -subj "/C=US/ST=CO/O=Connor_Arnold-Org/CN=Colorado Office Root"
```

### Verify the Root Certificate Authority

```bash
openssl x509 -in ColoradoOfficeRoot.crt -noout -subject -dates
openssl x509 -in ColoradoOfficeRoot.crt -noout -text | grep -E "Public-Key|Signature Algorithm"
```

## Quick Reference

| Item | Purpose |
|------|---------|
| Bash | Shell and scripting environment used to automate the Linux baseline |
| `hostnamectl` | Manages the system hostname |
| `timedatectl` | Displays and manages system time and time-zone configuration |
| `ps aux` | Lists running processes with detailed process information |
| `xfconf-query` | Reads and changes Xfce configuration properties |
| `xfce4-screensaver` | Provides screensaver and screen-lock functionality in Xfce |
| `/var/log/syslog` | General system log used as the source for recent security-related events |
| `tail -n 50` | Returns the final 50 lines of a file |
| `wc -l` | Counts lines in a file |
| OpenSSL | Cryptographic toolkit used to create and inspect the Certificate Authority |
| Advanced Encryption Standard 256-bit (AES-256) | Protected the root Certificate Authority private key |
| Rivest-Shamir-Adleman (RSA) | Asymmetric key algorithm used for the 4096-bit Certificate Authority key |
| Secure Hash Algorithm 256 (SHA-256) | Hash algorithm used when signing the Certificate Authority certificate |
| Certificate Authority (CA) | Establishes trust by signing and managing digital certificates |
| Certificate Signing Request (CSR) | Carries a public key and identity information to a Certificate Authority for certificate issuance |
| Public Key Infrastructure (PKI) | Framework for managing certificates, keys, trust, issuance, validation, and revocation |

## Related Playbook Pages

- [Bash Scripting Guide](../tools/bash-scripting-guide.md)
- [Bash Cheat Sheet](../tools/bash-cheat-sheet.md)
- [Certificate Authority (CA)](../../connection-security/concepts/certificate-authority.md)
- [Certificate Signing Requests (CSRs)](../../connection-security/concepts/csr-certificate-signing-requests.md)
- [Digital Certificates](../../connection-security/concepts/digital-certificates.md)
- [Key Management](../../connection-security/concepts/key-management.md)
- [Public Key Infrastructure (PKI)](../../connection-security/concepts/pki-public-key-infrastructure.md)
- [Advanced Encryption Standard (AES)](../../data-security/concepts/aes.md)
- [Rivest-Shamir-Adleman (RSA)](../../data-security/concepts/rsa.md)
- [Secure Hash Algorithm 256 (SHA-256)](../../data-security/concepts/sha-256.md)
- [System Hardening](../concepts/system-hardening.md) (coming soon)
