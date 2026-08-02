# Lab: GNS3 Network Reconfiguration Pre-Planning

CYB-310 5-3

## Overview

This lab demonstrated how to convert a current network topology and a future-state specification into a practical reconfiguration plan before implementation. The Graphical Network Simulator 3 (GNS3) environment was used to review the existing network, while the supplied specifications were used to determine future device counts, Virtual Local Area Network (VLAN) placement, addressing, and traffic paths through departmental switches, routers, the backbone, and the edge firewall.

## Lab Summary

This lab follows the lifecycle of network reconfiguration pre-planning:

1. Opened the Project Three Milestone environment in GNS3 and reviewed the current network topology.
2. Identified the existing departmental devices and their connections to the office, edge, and internet-facing infrastructure.
3. Reviewed the future-state specifications to determine the required computers, switches, servers, routers, VLANs, and Internet Protocol addresses.
4. Mapped the future traffic paths from each department and server network through the backbone and edge firewall.
5. Documented the planned future state in the Network Reconfiguration Planning Template for use during Project Three.

## Key Takeaways

- Pre-planning reduces configuration mistakes and troubleshooting during a timed network change.
- The current topology and the future-state specifications must be treated as separate network states.
- Departmental access switches aggregate endpoint connections before forwarding traffic to a router.
- VLANs separate Customer Experience, Human Resources, server, and backbone traffic into different broadcast domains.
- Each departmental subnet requires a router interface that acts as its default gateway.
- Separating departmental routing from server routing creates clearer traffic paths and security boundaries.
- A backbone switch provides a shared connection point for internal routers and the edge firewall.
- The edge firewall controls traffic between the internal network and the Wide Area Network (WAN).
- Device counts, interface assignments, and connection paths should be verified before implementation begins.

## Workflow

### Review the Current GNS3 Topology

The Project Three Milestone topology was opened in GNS3 and examined without changing any device configurations. The current network contained four Sales personal computers (PCs), three Customer Service PCs, one Customer Service File Transfer Protocol (FTP) server, four Human Resources (HR) PCs, three departmental switches, an Office Router, an Edge Router, an Edge Firewall, and an internet connection.

**Purpose**

- Establish an accurate baseline before planning changes.
- Identify the existing departmental structure and traffic path.
- Separate the current network state from the future-state design.

**Result**

- Sales devices connected through the Sales Switch.
- Customer Service devices and the FTP server connected through the Customer Service Switch.
- HR devices connected through the Human Resources Switch.
- The departmental switches connected to the Office Router, which connected through the Edge Router and Edge Firewall to the internet.

### Determine Future Device Requirements

The future-state network specifications were reviewed to determine the equipment required for the reconfigured organization.

**Purpose**

- Convert the organizational restructuring into specific device requirements.
- Ensure the planning template accounted for every required endpoint and network device.
- Prevent missing equipment from delaying the later implementation.

**Result**

- Customer Experience required six PCs and one switch.
- HR required three PCs and one switch.
- The server and backbone infrastructure required two servers, two switches, and two routers.
- The planned servers were the Web Server and Authentication Server.
- The planned infrastructure included the Customer Experience Switch, HR Switch, Server Switch, Backbone Switch, Core Router, and Server Router.

### Map the Future VLAN and Addressing Plan

The specifications divided the future network into four VLANs and four `/24` Internet Protocol version 4 (IPv4) networks.

**Purpose**

- Separate departmental and server traffic.
- Identify the correct router interfaces and default gateways.
- Provide a clear addressing reference for the later configuration exercise.

**Result**

- VLAN 1 used `192.168.1.0/24` for the backbone network.
- VLAN 2 used `192.168.2.0/24` for Customer Experience.
- VLAN 3 used `192.168.3.0/24` for HR.
- VLAN 4 used `192.168.4.0/24` for the server network.
- The Core Router provided the default gateways for Customer Experience and HR.
- The Server Router provided the default gateway for the server network.
- The Edge Firewall used `192.168.1.1` on the backbone-facing interface.

### Document the Future Backbone Connections

The future network connections were mapped from the endpoints to the WAN.

**Purpose**

- Visualize how traffic would move between departments, servers, and external networks.
- Define the physical and logical order of the network infrastructure.
- Prepare for later routing and firewall configuration.

**Result**

- Customer Experience PCs connected to the Customer Experience Switch.
- The Customer Experience Switch connected to the Core Router.
- HR PCs connected to the HR Switch.
- The HR Switch connected to the Core Router.
- The Web Server and Authentication Server connected to the Server Switch.
- The Server Switch connected to the Server Router.
- The Core Router and Server Router connected to the Backbone Switch.
- The Backbone Switch connected to the Edge Firewall.
- The Edge Firewall connected to the WAN cloud.

### Complete the Reconfiguration Planning Template

The verified device counts and connection paths were entered into the Network Reconfiguration Planning Template.

**Purpose**

- Create a concise implementation reference for Project Three.
- Satisfy the milestone requirements before beginning the timed reconfiguration.
- Provide a document that could be reviewed and corrected before the final project.

**Result**

- The completed plan documented the Customer Experience, HR, server, router, switch, and backbone requirements.
- No device configuration was performed because this milestone focused on pre-planning.

## Notes

### Current State and Future State

| Area | Current State | Planned Future State |
|------|---------------|----------------------|
| Sales / Customer Experience | Four Sales PCs and one Sales Switch | Six Customer Experience PCs and one Customer Experience Switch |
| Customer Service | Three PCs, one FTP server, and one switch | Replaced by the Customer Experience and dedicated server networks |
| Human Resources | Four PCs and one switch | Three PCs and one HR Switch |
| Servers | One Customer Service FTP server | Web Server and Authentication Server |
| Internal Routing | Office Router and Edge Router | Core Router and Server Router |
| Backbone | Departmental switches connected to the Office Router | Core Router and Server Router connected through the Backbone Switch |
| Network Edge | Edge Router to Edge Firewall to internet | Backbone Switch to Edge Firewall to WAN |

### Planned Traffic Flow

```text
Customer Experience PCs
        |
Customer Experience Switch
        |
     Core Router -------- HR Switch -------- HR PCs
        |
   Backbone Switch
        |
    Edge Firewall
        |
      WAN Cloud

Web Server ----\
                Server Switch ---- Server Router
Auth Server ---/                         |
                                  Backbone Switch
```

### Planning Scope

This milestone documented what the future network should contain and how it should be connected. Internet Protocol addressing, VLAN configuration, routing, connectivity testing, and firewall rules were reserved for the later Project Three implementation.

## Commands Used

No command-line commands were required. The assignment was completed by reviewing the GNS3 topology, examining the supplied network specifications, and documenting the planned future state.

## Quick Reference

| Item | Purpose |
|------|---------|
| GNS3 | Displays and simulates the network topology |
| VLAN 1 | Backbone network using `192.168.1.0/24` |
| VLAN 2 | Customer Experience network using `192.168.2.0/24` |
| VLAN 3 | HR network using `192.168.3.0/24` |
| VLAN 4 | Server network using `192.168.4.0/24` |
| Core Router | Routes Customer Experience and HR traffic |
| Server Router | Routes traffic for the server network |
| Backbone Switch | Connects internal routers to the edge firewall |
| Edge Firewall | Controls traffic between the internal network and WAN |
| Default gateway | Router interface used to reach other networks |
| `/24` subnet | Provides the subnet mask `255.255.255.0` |

## Related Playbook Pages

- [Firewalls](../concepts/firewalls.md)
- [IPv4 Addressing](../concepts/ipv4-addressing.md)
- [Subnetting](../concepts/subnetting.md)
- [TCP/IP](../concepts/tcp-ip.md)
- [Virtual Local Area Networks (VLANs)](../concepts/vlans-virtual-local-area-networks.md) (coming soon)
- [GNS3](../tools/gns3.md) (coming soon)
