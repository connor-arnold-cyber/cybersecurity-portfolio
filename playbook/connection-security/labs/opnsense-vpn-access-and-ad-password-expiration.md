# Lab: OPNsense VPN Access Restriction and Active Directory Password Expiration

CYB-310 Project One: Network Evaluation Report

## Overview

This lab evaluated two network-security weaknesses in a GNS3 environment: an overly broad VPN firewall rule that allowed a remote-access computer to reach the internal network and Active Directory accounts configured so their passwords never expired. The lab focused on applying least privilege, validating account-level policy settings, restricting network access with OPNsense, and verifying the results without changing unrelated configurations.

## Lab Summary

This lab follows the lifecycle of identifying and correcting excessive network and account privileges:

1. Reviewed the GNS3 topology and documented the IP configuration of the remote-access computer, FTP server, firewall, and Active Directory server.
2. Checked the Default Domain Policy and discovered that account-level password settings were overriding the existing expiration policy.
3. Changed `PasswordNeverExpires` from `True` to `False` for the affected Active Directory accounts and verified the result.
4. Confirmed that the remote-access computer could reach an unrelated internal Active Directory server before the firewall change.
5. Replaced the broad OPNsense VPN pass rule with a rule limited to one source host and one destination host.
6. Verified that the remote-access computer could no longer reach the Active Directory server after the rule was applied.
7. Confirmed that the FTP service was listening on TCP port 21, while documenting that the end-to-end FTP connection still timed out in the lab environment.

## Key Takeaways

- A correct domain password policy can still be bypassed by account-level settings.
- `PasswordNeverExpires=True` prevents the maximum password age from applying to an account.
- A `/32` prefix identifies one specific IPv4 host.
- Broad allow rules create unnecessary access and violate least privilege.
- Default-deny firewall behavior makes a narrow allow rule more effective than multiple block rules.
- Verification should test both the access that must be blocked and the service that must remain available.
- A listening service does not guarantee successful end-to-end connectivity.
- Failed FTP connectivity can result from routing, return-path, or host-firewall issues outside the VPN rule itself.

## Workflow

### Document the Network Environment

The GNS3 topology was reviewed to identify the systems involved in both challenges. IP configuration was collected from the remote-access computer, FTP server, Active Directory server, and OPNsense firewall interfaces.

**Purpose**

- Establish the source and destination addresses required for the firewall rule.
- Identify an unrelated internal system for before-and-after access testing.
- Confirm which network interfaces connected the VPN and internal networks.

**Result**

- Remote-access computer: `172.16.3.1`
- OPNsense VPN interface: `172.16.3.254/24`
- FTP server: `172.16.2.1`
- Active Directory server: `192.168.10.5`
- OPNsense LAN interface: `10.10.10.254/24`
- OPNsense WAN interface: `192.168.122.126/24`

### Evaluate the Password Configuration

The Default Domain Policy and individual Active Directory account properties were checked. The domain already enforced password complexity, remembered 24 previous passwords, and used a maximum password age of 42 days. A PowerShell query showed that the enabled user accounts had `PasswordNeverExpires` set to `True`.

**Purpose**

- Determine whether the weakness came from the domain policy or account-level configuration.
- Avoid changing a domain policy that was already configured correctly.
- Identify the exact accounts affected by the exemption.

**Result**

- The domain policy was already configured.
- Fourteen accounts were exempted from password expiration.

### Correct the Password Expiration Settings

The affected account names were placed into a PowerShell array. `Set-ADUser` was then used to change `PasswordNeverExpires` to `False` for each account.

**Purpose**

- Allow the existing 42-day maximum password age to apply.
- Correct only the affected account property.
- Preserve the existing complexity and password-history settings.

**Result**

- All fourteen listed accounts showed `PasswordNeverExpires=False` during verification.

### Test Remote Access Before the Firewall Change

The remote-access computer was tested against the Active Directory server at `192.168.10.5`. Ping and traceroute both succeeded before the VPN rule was changed.

**Purpose**

- Prove that the remote-access computer could reach an unrelated internal server.
- Establish a clear before state for the access-control issue.
- Confirm that the problem was not limited to one application or protocol.

**Result**

- The remote-access computer reached the Active Directory server through the internal network.

### Restrict the OPNsense VPN Rule

The VPN interface contained a broad IPv4 pass rule. The rule was edited so that only the remote-access computer could communicate with the designated FTP server.

**Purpose**

- Apply least privilege to the remote-access connection.
- Remove access to unrelated internal systems.
- Use the firewall's default-deny behavior instead of creating separate block rules for every internal network.

**Result**

- Action: `Pass`
- Interface: `VPN`
- Direction: `in`
- TCP/IP version: `IPv4`
- Protocol: `any`
- Source: `172.16.3.1/32`
- Destination: `172.16.2.1/32`
- Destination ports: `any`
- Description: `allow remote access pc to ftp server only`

### Verify the Firewall Restriction

After the rule was saved and applied, the remote-access computer was tested against the Active Directory server again.

**Purpose**

- Confirm that the new rule blocked access outside the approved destination.
- Verify that the firewall change affected the intended traffic.
- Demonstrate that the broad internal access had been removed.

**Result**

- Ping requests to `192.168.10.5` timed out after the firewall change.

### Verify the FTP Service

The FTP server was checked locally with `netstat` to determine whether TCP port 21 was listening. Connection attempts from the remote-access computer were also tested.

**Purpose**

- Separate a service-state problem from a firewall-rule problem.
- Confirm that the FTP service existed on the designated server.
- Document the remaining connectivity limitation without reopening broad access.

**Result**

- The FTP server was listening on TCP port 21.
- FTP, ping, and traceroute attempts from the remote-access computer to `172.16.2.1` timed out.
- The remaining FTP issue was not resolved during the lab and could involve routing, return traffic, or the FTP server's host firewall.

## Notes

### Least-Privilege Rule Design

The original rule allowed traffic from any source to any destination. The replacement rule allowed only one specific source and one specific destination:

```text
Remote_Access_PC                      RAFTP
172.16.3.1/32  -------------------->  172.16.2.1/32
                    OPNsense VPN rule

All other destinations: denied by the firewall's default policy
```

Using one narrow pass rule was safer and easier to maintain than creating individual block rules for every internal host or network.

### Domain Policy Versus Account-Level Settings

The domain password policy defined the general requirements, but the `PasswordNeverExpires` property exempted individual accounts from the maximum password age. Correcting the account property allowed the existing domain policy to work as intended.

### FTP Verification Limitation

The local `netstat` result confirmed that the FTP service was listening. However, the remote FTP test timed out. A complete follow-up investigation would check Windows Firewall rules on the FTP server, routing between `172.16.3.0/24` and `172.16.2.0/24`, return routes, OPNsense logs, and any intermediate firewall rules. The VPN rule should remain narrow during that investigation.

## Commands Used

### Identify Accounts With Passwords That Never Expire

```bash
Get-ADUser -Filter * -Properties Enabled,PasswordNeverExpires |
Where-Object { $_.Enabled -eq $true -and $_.PasswordNeverExpires -eq $true } |
Select Name,SamAccountName,PasswordNeverExpires |
Format-Table -AutoSize
```

### Correct Password Expiration Settings

```bash
$accounts = 'ITPC1','ITPC2','ITPC3','ITPC4','PROFPC1','PROFPC2','PROFPC3','AAPC1','AAPC2','AAPC3','AAPC4','AAAdmin','ProfAdmin','ITAdmin'
```

```bash
$accounts | ForEach-Object { Set-ADUser -Identity $_ -PasswordNeverExpires $false }
```

### Verify Password Expiration Settings

```bash
$accounts |
ForEach-Object {
    Get-ADUser -Identity $_ -Properties PasswordNeverExpires
} |
Select Name,SamAccountName,PasswordNeverExpires |
Format-Table -AutoSize
```

### Document IP Configuration and Local Network Information

```bash
ipconfig
```

```bash
route print
```

```bash
arp -a
```

### Test Internal Access Before the Firewall Change

```bash
ping 192.168.10.5
```

```bash
tracert -d 192.168.10.5
```

### Verify Internal Access Was Blocked

```bash
echo Connor Arnold
ping -n 2 192.168.10.5
```

### Test FTP Connectivity

```bash
powershell -Command "Test-NetConnection 172.16.2.1 -Port 21 -InformationLevel Quiet"
```

```bash
ftp 172.16.2.1
```

```bash
tracert -d 172.16.2.1
```

```bash
ping -n 2 172.16.2.1
```

### Verify the FTP Service Was Listening

```bash
netstat -ano | findstr ":21"
```

## Quick Reference

| Item | Purpose |
|------|---------|
| OPNsense | Firewall platform used to restrict VPN traffic |
| VPN interface | Entry point for the remote-access computer |
| `172.16.3.1/32` | Single source host allowed by the rule |
| `172.16.2.1/32` | Single destination host allowed by the rule |
| `/32` | Classless Inter-Domain Routing prefix for one IPv4 address |
| `PasswordNeverExpires` | Active Directory property that can bypass password expiration |
| `Get-ADUser` | Retrieves Active Directory account properties |
| `Set-ADUser` | Changes Active Directory account properties |
| TCP port 21 | FTP control connection port |
| Default deny | Blocks traffic that does not match an allow rule |

## Related Playbook Pages

- [Active Directory](../concepts/active-directory.md)
- [Authentication](../concepts/authentication.md)
- [CIDR](../concepts/cidr.md)
- [Firewalls](../concepts/firewalls.md)
- [IPv4 Addressing](../concepts/ipv4-addressing.md)
- [Ports and Port Numbers](../concepts/ports-and-port-numbers.md)
- [VPN](../concepts/vpn-virtual-private-network.md)
- [Ping](../tools/ping.md)
- [Traceroute](../tools/traceroute.md)
- [PowerShell Cheat Sheet](../../system-security/tools/powershell-cheat-sheet.md)
