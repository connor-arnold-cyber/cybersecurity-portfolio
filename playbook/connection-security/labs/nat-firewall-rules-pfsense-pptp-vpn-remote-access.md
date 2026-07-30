# Lab: NAT, pfSense Firewall Rules, and PPTP VPN Remote Access

## Overview

This lab demonstrated how Network Address Translation, firewall rules, traffic-analysis tools, and a remote-access VPN work together to control communication between private and public networks while allowing an authorized external user to connect to an internal network.

## Lab Summary

This lab follows the lifecycle of NAT and remote-access VPN configuration:

1. Verify and analyze communication between internal and external hosts using Ping, Nmap, and Wireshark.
2. Modify pfSense LAN firewall rules and confirm how the changes affect NAT connectivity.
3. Enable VPN access on a Windows Server and authorize an Active Directory account for remote access.
4. Redirect PPTP traffic through pfSense and establish a VPN connection from an external Windows system.

## Key Takeaways

- NAT allows privately addressed hosts to communicate with public networks through a translated address.
- Firewall rules determine whether translated traffic is permitted to cross network boundaries.
- Nmap identifies externally accessible ports and services, while Wireshark provides packet-level visibility.
- Connectivity testing before and after a firewall change helps confirm the effect of the configuration.
- Remote-access VPNs allow authenticated external users to reach resources on a private network.
- VPN access requires coordinated configuration across the firewall, VPN server, user account, and client.
- PPTP is a legacy VPN protocol and should be replaced by a modern secure protocol in production environments.

## Workflow

### Verify NAT Connectivity

Ping was used from the internal Windows 10 system to verify connectivity with the external Windows 8.1 host before firewall rules were modified.

**Purpose**

- Confirm that the internal system could communicate with the external network.
- Establish a known working state before configuration changes.
- Provide a baseline for later connectivity tests.

**Result**

- The internal system successfully received replies from the external host at `175.45.176.200`.

### Capture and Filter Network Traffic

Wireshark captured the ping traffic on the internal system, and a display filter isolated packets sent to the external host.

**Purpose**

- Observe the packets generated during the connectivity test.
- Identify source and destination addressing.
- Verify that traffic was reaching the intended external system.

**Result**

- Wireshark displayed packets with `175.45.176.200` as the destination address.

### Scan the Firewall

Nmap was run from the external Windows 8.1 machine against the pfSense WAN address.

**Purpose**

- Identify ports exposed on the firewall.
- Examine the network from an external perspective.
- Establish which services were reachable before remote access was configured.

**Result**

- Nmap reported the ports and services that were accessible through the pfSense WAN interface.

### Analyze Externally Visible Traffic

Wireshark was used on the external machine to inspect traffic associated with communication through NAT.

**Purpose**

- Compare external packet information with the internal traffic capture.
- Observe the translated address visible from the WAN.
- Confirm that private internal addressing was not exposed to the external host.

**Result**

- The external system observed traffic originating from the firewall's public-facing address rather than the private address of the internal host.

### Remove Existing LAN Firewall Rules

The existing pfSense LAN firewall rules were deleted and the configuration changes were applied.

**Purpose**

- Demonstrate the relationship between firewall policy and NAT connectivity.
- Test how removing an allow rule affects outbound communication.
- Create a controlled failure state for comparison.

**Result**

- Ping requests from the internal system to the external host timed out after the LAN rules were removed.

### Create an Allow Rule

A new pfSense LAN rule was created with the protocol set to `any`, and the configuration was applied.

**Purpose**

- Restore permitted communication from the LAN to the WAN.
- Demonstrate how firewall rules control translated traffic.
- Verify that an explicit rule change produced the expected network behavior.

**Result**

- The internal Windows 10 system could successfully ping the external host again.

### Enable Routing and Remote Access

Routing and Remote Access was configured on the internal Windows Server using a custom configuration with VPN access enabled.

**Purpose**

- Prepare the server to accept remote VPN connections.
- Provide an internal endpoint for authenticated remote users.
- Enable remote access to the private network.

**Result**

- The Routing and Remote Access service started with VPN access enabled.

### Authorize the Administrator Account

Active Directory Users and Computers was opened, and dial-in access was allowed for the Administrator account.

**Purpose**

- Permit the account to authenticate through the VPN service.
- Connect remote-access authorization to an Active Directory identity.
- Prevent unauthorized accounts from using the VPN connection.

**Result**

- The Administrator account was authorized for remote access.

### Configure PPTP Redirection

The pfSense PPTP settings were configured to redirect incoming PPTP connections to the internal Windows Server at `192.168.1.10`.

**Purpose**

- Forward incoming VPN traffic from the WAN interface to the VPN server.
- Connect the public-facing firewall to the private VPN endpoint.
- Allow the external client to reach the internal remote-access service.

**Result**

- Incoming PPTP connections were redirected to the Windows Server.

### Create the External VPN Connection

A workplace VPN connection was created on the external Windows 8.1 machine using `203.0.113.100` as the Internet address.

**Purpose**

- Configure the external system with the public address of the VPN gateway.
- Create a client connection capable of reaching the private network.
- Prepare the VPN client for PPTP authentication.

**Result**

- A VPN connection named `VPN Connection` was added to the external system.

### Configure and Establish the PPTP VPN

The client VPN type was changed to PPTP, allowed authentication protocols were enabled, and the Administrator account was used to connect.

**Purpose**

- Match the client VPN protocol to the server and firewall configuration.
- Authenticate an authorized remote user.
- Verify end-to-end remote connectivity through the firewall.

**Result**

- The Windows network panel displayed `VPN Connection` with a status of `Connected`.

## Notes

### NAT and Firewall Rules

NAT translates addresses, but it does not independently guarantee that traffic will be permitted. A corresponding firewall policy must allow the traffic to pass. The lab demonstrated this by removing the LAN rules, observing failed pings, creating a new allow rule, and confirming that connectivity returned.

### Remote-Access Path

```text
External Windows 8.1 Client
        175.45.176.200
               |
               | PPTP VPN connection
               v
       pfSense WAN Interface
         203.0.113.100
               |
               | PPTP redirection
               v
     Internal Windows Server
          192.168.1.10
               |
               | Authenticated access
               v
        Private LAN Resources
```

### Nmap and Wireshark

Nmap provided a high-level view of reachable ports and services, while Wireshark showed the individual packets exchanged across the network. Using them together connected scan results with the actual traffic that produced those results.

### PPTP Security

PPTP was used to demonstrate the remote-access configuration process, but it is a legacy VPN protocol with known security weaknesses. Modern environments should use stronger alternatives such as IPsec, OpenVPN, WireGuard, or a properly configured TLS-based VPN.

## Commands Used

### Test NAT Connectivity

```cmd
ping 175.45.176.200
ping 175.45.176.200 -t
```

### Scan the Firewall

```cmd
nmap 203.0.113.100
```

### Open Active Directory Users and Computers

```cmd
dsa.msc
```

## Quick Reference

| Item | Purpose |
|------|---------|
| NAT | Translate between private and public IP addresses |
| pfSense | Provide firewall, NAT, and VPN traffic-redirection functions |
| LAN firewall rule | Permit or deny traffic leaving the internal network |
| Ping | Verify IP connectivity between hosts |
| Nmap | Identify accessible ports and services |
| Wireshark | Capture and inspect network packets |
| Routing and Remote Access | Provide Windows Server routing and VPN services |
| Active Directory dial-in access | Authorize a user account for remote access |
| PPTP | Establish the lab's remote-access VPN tunnel |
| `203.0.113.100` | Public-facing VPN and firewall address |
| `192.168.1.10` | Internal Windows VPN server address |
| `175.45.176.200` | External Windows client address |

## Related Playbook Pages

- [Network Address Translation (NAT)](../concepts/network-address-translation-nat.md) (coming soon)
- [Firewalls](../concepts/firewalls.md)
- [Virtual Private Network (VPN)](../concepts/vpn-virtual-private-network.md)
- [Point-to-Point Tunneling Protocol (PPTP)](../concepts/pptp-point-to-point-tunneling-protocol.md) (coming soon)
- [IPv4 Addressing](../concepts/ipv4-addressing.md)
- [Internet Control Message Protocol (ICMP)](../concepts/icmp.md)
- [Port Scanning](../concepts/port-scanning.md)
- [Packet Sniffing](../concepts/packet-sniffing.md)
- [Active Directory](../concepts/active-directory.md)
- [Nmap](../tools/nmap.md)
- [Wireshark](../tools/wireshark.md)
- [Ping](../tools/ping.md)
- [pfSense](../tools/pfsense.md) (coming soon)
- [Routing and Remote Access Service (RRAS)](../tools/routing-and-remote-access-service-rras.md) (coming soon)
