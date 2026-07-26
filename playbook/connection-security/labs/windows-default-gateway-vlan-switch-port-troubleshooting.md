# Lab: Troubleshoot Windows Default Gateway and VLAN Switch-Port Misconfigurations

## Overview

This lab demonstrated a structured process for troubleshooting Windows network-connectivity failures caused by incorrect default gateways and switch-port VLAN assignments. A working Human Resources workstation was used as a baseline, failed workstations were examined with Windows networking commands, and the Human Resources switch configuration was compared against the expected VLAN. Correcting the Layer 3 gateway settings and Layer 2 VLAN assignments restored connectivity without modifying the workstation that was already functioning.

## Lab Summary

This lab follows the lifecycle of network-connectivity troubleshooting:

1. Establish the expected Human Resources network configuration using a known-working workstation.
2. Inspect the failed workstations and test local and external connectivity.
3. Identify incorrect default gateways and switch-port VLAN assignments.
4. Correct the configurations, clear stale network information, and repeat the connectivity tests.

## Key Takeaways

- A known-working device provides reliable baseline values for troubleshooting similar systems.
- A default gateway must identify a reachable router on the host's local subnet.
- A host can communicate with local addresses even when its configured default gateway is incorrect.
- Access switch ports must be assigned to the correct VLAN for Layer 2 communication.
- Incorrect gateway and VLAN settings can exist on the same workstation simultaneously.
- Ping results can help distinguish local network failures from routing failures.
- ARP information may need to be cleared after a Layer 2 configuration change.
- Every configuration correction should be followed by repeat testing.

## Workflow

### Establish a Known-Working Baseline

HR_PC1 was inspected first because it was the only Human Resources workstation with working cloud connectivity.

**Purpose**

- Identify the expected Human Resources IP addressing configuration.
- Determine the correct subnet mask and default gateway.
- Establish a known-good configuration for comparison.
- Avoid modifying a workstation that was already functioning.

**Result**

- HR_PC1 was connected to the `192.168.30.0/24` network.
- The expected subnet mask was `255.255.255.0`.
- The correct default gateway was `192.168.30.254`.
- The working Human Resources switch ports used VLAN 30.

### Inspect HR_PC2

The IP configuration and connectivity of HR_PC2 were examined with `ipconfig` and `ping`.

**Purpose**

- Compare HR_PC2 against the known-working workstation.
- Determine whether the failure involved addressing, routing, switching, or multiple layers.
- Record the original failure state before making changes.

**Result**

- HR_PC2 used the IP address `192.168.30.2`.
- Its default gateway was incorrectly configured as `192.168.30.252`.
- HR_PC2 could not reach `192.168.30.254`.
- HR_PC2 could not reliably reach the external address `1.1.1.1`.
- Switch port 2 was assigned to VLAN 10 instead of VLAN 30.

### Inspect HR_PC3

The IP configuration and connectivity of HR_PC3 were compared with the known-working baseline.

**Purpose**

- Determine whether HR_PC3 had the same failure as HR_PC2.
- Test local-subnet communication separately from external communication.
- Identify whether the switch port or default gateway was responsible.

**Result**

- HR_PC3 used the IP address `192.168.30.3`.
- Its default gateway was incorrectly configured as `192.168.30.250`.
- HR_PC3 successfully reached `192.168.30.254` because the address was on the same local `/24` network.
- HR_PC3 could not reach `1.1.1.1` because external traffic was sent toward the incorrect gateway.
- HR_PC3's switch port was already assigned to VLAN 30.

### Inspect HR_PC4

HR_PC4 was compared against the expected Human Resources configuration and the switch-port assignments.

**Purpose**

- Determine whether HR_PC4 had an incorrect host configuration.
- Identify a possible Layer 2 configuration problem.
- Compare its connected switch port with the working VLAN assignments.

**Result**

- No default-gateway error was identified for HR_PC4.
- Switch port 4 was assigned to VLAN 20 instead of VLAN 30.
- The incorrect VLAN logically separated HR_PC4 from the Human Resources network.

### Inspect the Human Resources Switch

The port table on the Human Resources switch was reviewed and compared with the known-working Human Resources ports.

**Purpose**

- Identify ports assigned to the wrong VLAN.
- Determine whether failed workstations were logically connected to another department's network.
- Separate switch configuration errors from workstation addressing errors.

**Result**

- Ports 0 and 1 were assigned to VLAN 30.
- Port 2 was incorrectly assigned to VLAN 10.
- Port 3 was assigned to VLAN 30.
- Port 4 was incorrectly assigned to VLAN 20.
- Ports 5 through 7 remained unused access ports on the default VLAN 1.

### Correct the HR_PC2 Default Gateway

HR_PC2 was reconfigured to use `192.168.30.254` as its default gateway.

**Purpose**

- Replace the incorrect gateway with the Human Resources router address.
- Match the known-working addressing configuration.
- Restore the ability to route traffic outside the local subnet.

**Result**

- HR_PC2 retained the IP address `192.168.30.2`.
- The subnet mask remained `255.255.255.0`.
- The default gateway changed from `192.168.30.252` to `192.168.30.254`.

### Correct the HR_PC3 Default Gateway

HR_PC3 was reconfigured to use the correct Human Resources default gateway.

**Purpose**

- Replace the nonexistent or incorrect gateway address.
- Allow HR_PC3 to forward traffic beyond the local subnet.
- Match the working HR_PC1 network configuration.

**Result**

- HR_PC3 retained the IP address `192.168.30.3`.
- The subnet mask remained `255.255.255.0`.
- The default gateway changed from `192.168.30.250` to `192.168.30.254`.

### Correct the Switch VLAN Assignments

The incorrect port 2 VLAN 10 and port 4 VLAN 20 entries were removed. Both ports were then added back as access ports on VLAN 30.

**Purpose**

- Place HR_PC2 and HR_PC4 on the Human Resources VLAN.
- Restore Layer 2 communication with the Human Resources gateway.
- Remove the logical separation caused by the incorrect VLAN assignments.
- Make the failed switch ports match the working Human Resources ports.

**Result**

- Ports 0 through 4 were configured as access ports on VLAN 30.
- HR_PC2 was moved from VLAN 10 to VLAN 30.
- HR_PC4 was moved from VLAN 20 to VLAN 30.
- The Human Resources workstations and gateway were placed in the same Layer 2 broadcast domain.

### Clear ARP Information

Cached ARP entries were cleared after the VLAN changes.

**Purpose**

- Remove address mappings learned before the switch configuration was corrected.
- Force the workstations to discover current MAC address information.
- Prevent stale Layer 2 information from affecting the verification tests.

**Result**

- The workstations could relearn the MAC address associated with the Human Resources gateway.
- Connectivity testing was performed against the corrected configuration.

### Verify HR_PC2 Connectivity

The updated HR_PC2 configuration was reviewed, and connectivity tests were repeated.

**Purpose**

- Confirm that the new default gateway was applied.
- Verify local communication with the Human Resources gateway.
- Verify communication beyond the local network.

**Result**

- `ipconfig` showed `192.168.30.254` as the default gateway.
- HR_PC2 successfully reached `192.168.30.254` with zero percent packet loss.
- An initial external test timed out in the virtual environment.
- A repeated test successfully reached `1.1.1.1` with zero percent packet loss.

### Verify HR_PC3 Connectivity

The corrected HR_PC3 configuration was reviewed and tested.

**Purpose**

- Confirm that the incorrect gateway was replaced.
- Verify that local connectivity remained functional.
- Confirm that external routing was restored.

**Result**

- `ipconfig` showed `192.168.30.254` as the default gateway.
- HR_PC3 successfully reached `192.168.30.254`.
- HR_PC3 successfully reached `1.1.1.1`.
- Both tests completed with zero percent packet loss.

### Verify the Final Switch Configuration

The Human Resources switch configuration was reviewed after the VLAN corrections.

**Purpose**

- Confirm that the incorrect VLAN entries were removed.
- Verify that all connected Human Resources ports used VLAN 30.
- Ensure that no duplicate or conflicting port entries remained.

**Result**

- Ports 0 through 4 appeared as access ports on VLAN 30.
- Port 2 was no longer assigned to VLAN 10.
- Port 4 was no longer assigned to VLAN 20.
- HR_PC4's connected port was restored to the Human Resources VLAN.

## Notes

### Known-Good Baseline Comparison

Using HR_PC1 as a baseline provided expected values for the IP network, subnet mask, default gateway, and VLAN. This reduced unnecessary changes because each failed workstation could be compared against a configuration that was already proven to work.

### Default Gateway Behavior

A default gateway is used only when a host needs to send traffic outside its local subnet. Devices determine whether a destination is local by comparing the destination address with their own IP address and subnet mask.

HR_PC3 could reach `192.168.30.254` even though its configured gateway was `192.168.30.250`. The destination `192.168.30.254` was inside the same `192.168.30.0/24` network, so HR_PC3 contacted it directly through ARP rather than using its configured default gateway.

Traffic for `1.1.1.1` was outside the local subnet. HR_PC3 therefore attempted to forward the traffic to the incorrect gateway at `192.168.30.250`, causing the external test to fail.

### VLAN Access Ports

An access port places untagged traffic from a connected endpoint into one VLAN. Devices connected to different VLANs are logically separated even when they are attached to the same physical switch.

HR_PC2 and HR_PC4 were physically connected to the Human Resources switch but were assigned to VLANs 10 and 20. Moving their ports to VLAN 30 placed them in the same broadcast domain as the other Human Resources systems and the gateway.

### Layer 2 and Layer 3 Failures

HR_PC2 contained both a Layer 2 and a Layer 3 error:

```text
HR_PC2
   |
   +--> Layer 2 Error: Switch Port 2 Assigned to VLAN 10
   |
   +--> Layer 3 Error: Default Gateway Set to 192.168.30.252
```

Correcting only one of these errors would not have fully restored external connectivity. The switch port had to be moved to VLAN 30, and the default gateway had to be changed to `192.168.30.254`.

### Troubleshooting Path

```text
Start With Known-Working HR_PC1
               |
               v
Record Expected IP, Mask, Gateway, and VLAN
               |
               v
Inspect HR_PC2, HR_PC3, and HR_PC4
               |
               v
Ping 192.168.30.254
               |
        +------+------+
        |             |
     Success        Failure
        |             |
        v             v
Test 1.1.1.1    Inspect Host and Switch
        |             |
        v             v
Check Gateway    Correct VLAN Assignment
        |             |
        +------+------+
               |
               v
Correct Default Gateways
               |
               v
Clear ARP Information
               |
               v
Repeat Gateway and External Tests
```

### Verification Scope

The resolution evidence directly demonstrated successful gateway and external pings from HR_PC2 and HR_PC3. HR_PC4's correction was demonstrated through the final switch configuration, which showed its connected port assigned to VLAN 30. A separate post-correction HR_PC4 ping was not included in the submitted screenshots.

### Virtual Environment Connectivity

The first external ping from HR_PC2 after the corrections timed out, but the repeated test successfully reached `1.1.1.1` with zero percent packet loss. The stable gateway test and successful repeated external test showed that the addressing and VLAN corrections had been applied even though the virtual lab briefly produced an intermittent external timeout.

## Commands Used

### Inspect IP Configuration

```cmd
ipconfig
ipconfig /all
```

### Test Local and External Connectivity

```cmd
ping 192.168.30.254
ping 1.1.1.1
```

### Correct HR_PC2 Addressing

```cmd
netsh interface ipv4 set address name="Ethernet" static 192.168.30.2 255.255.255.0 192.168.30.254
```

### Correct HR_PC3 Addressing

```cmd
netsh interface ipv4 set address name="Ethernet" static 192.168.30.3 255.255.255.0 192.168.30.254
```

### Clear Cached ARP Information

```cmd
arp -d *
```

### Verify the Corrected Configuration

```cmd
ipconfig
ping 192.168.30.254
ping 1.1.1.1
```

## Quick Reference

| Item | Purpose |
|------|---------|
| HR_PC1 | Provide the known-working troubleshooting baseline |
| HR_PC2 | Workstation with an incorrect gateway and VLAN assignment |
| HR_PC3 | Workstation with an incorrect default gateway |
| HR_PC4 | Workstation connected through an incorrectly assigned VLAN |
| `192.168.30.0/24` | Human Resources IPv4 network |
| `255.255.255.0` | Human Resources subnet mask |
| `192.168.30.254` | Correct Human Resources default gateway |
| `1.1.1.1` | External Cloud IP used for connectivity testing |
| VLAN 30 | Human Resources VLAN |
| VLAN 10 | Incorrect initial VLAN for switch port 2 |
| VLAN 20 | Incorrect initial VLAN for switch port 4 |
| Access port | Assign a connected endpoint to one VLAN |
| `ipconfig` | Display Windows IP configuration |
| `ping` | Test ICMP reachability and packet loss |
| `netsh` | Modify Windows network-interface settings |
| `arp -d *` | Delete cached ARP mappings |

## Related Playbook Pages

- [IPv4 Addressing](../concepts/ipv4-addressing.md)
- [Subnetting](../concepts/subnetting.md)
- [Internet Control Message Protocol (ICMP)](../concepts/icmp.md)
- [Ping](../tools/ping.md)
- [Traceroute](../tools/traceroute.md)
- [Virtual Local Area Networks (VLANs)](../concepts/vlan-virtual-local-area-network.md) (coming soon)
- [Address Resolution Protocol (ARP)](../concepts/arp-address-resolution-protocol.md) (coming soon)
- [GNS3](../tools/gns3.md) (coming soon)
