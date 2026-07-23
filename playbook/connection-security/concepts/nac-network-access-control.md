# Network Access Control (NAC)

## Overview

Network Access Control (NAC) is a security solution that controls whether users and devices are allowed to connect to a network. Before granting access, NAC verifies the identity of the user or device and evaluates whether it complies with the organization's security policies.

NAC helps prevent unauthorized or non-compliant devices from accessing network resources.

## Key Concepts

### Authentication

Before a device joins the network, NAC verifies its identity.

Authentication may use:

- Username and password
- Digital certificates
- Multi-Factor Authentication (MFA)
- 802.1X authentication

Only authenticated users and devices are considered for network access.

### Device Compliance

NAC can evaluate the security posture of a device before granting access.

Common checks include:

- Operating system version
- Installed security patches
- Antivirus status
- Firewall status
- Endpoint protection software
- Device configuration

Devices that fail compliance checks may be denied access or placed into a restricted network.

### Access Policies

Organizations define policies that determine what level of access a device receives.

Examples include:

- Full network access
- Guest network access
- Limited access to remediation servers
- Complete denial of access

Policies may be based on the user's identity, device type, location, or security posture.

### Network Segmentation

NAC often works with VLANs or other segmentation technologies.

After authentication, compliant devices can be placed into the appropriate network segment while guest or unmanaged devices are isolated.

### Continuous Monitoring

Some NAC solutions continue monitoring connected devices.

If a device later becomes non-compliant, NAC can:

- Restrict access
- Move the device to a quarantine network
- Disconnect the device entirely

## Why It Matters

Unauthorized or vulnerable devices represent a significant security risk. NAC helps organizations ensure that only trusted users and compliant devices gain access to network resources, reducing the likelihood of malware infections, unauthorized access, and policy violations.

## Common Uses

- Enterprise networks
- Corporate Wi-Fi
- Wired networks
- Guest networks
- Bring Your Own Device (BYOD)
- Healthcare environments
- Educational institutions

## Best Practices

- Integrate NAC with centralized authentication services.
- Require strong authentication before granting network access.
- Enforce device compliance checks.
- Segment guest and unmanaged devices from internal resources.
- Continuously monitor connected devices for policy compliance.
