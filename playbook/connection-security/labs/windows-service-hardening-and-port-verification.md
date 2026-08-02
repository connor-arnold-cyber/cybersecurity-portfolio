# Lab: Windows Service Hardening and Port Verification

CYB-310 5-1

## Overview

This lab demonstrated how exposed network services can be identified, tested, disabled, and verified to reduce a system's attack surface. A Kali Linux system used Telnet and Nmap to test a Windows Server, and the World Wide Web Publishing Service was stopped and disabled so TCP port 80 could be confirmed closed.

## Lab Summary

This lab follows the lifecycle of network service exposure and hardening:

1. Connected from Kali Linux to the Windows Server's HTTP service on TCP port 80 using Telnet.
2. Sent an HTTP `HEAD` request and confirmed that Microsoft Internet Information Services responded.
3. Opened the Windows Services console and disabled the World Wide Web Publishing Service.
4. Scanned TCP port 80 with Nmap and found that the service was still listening after the first stop attempt.
5. Corrected the service state, rescanned the server, and verified that TCP port 80 was closed.

## Key Takeaways

- Every unnecessary open port increases the system's attack surface.
- A service can remain reachable until it is both stopped and prevented from restarting.
- Telnet can test whether a TCP service accepts connections, but Telnet itself does not encrypt traffic.
- An HTTP error response still proves that the web service received and processed the request.
- Nmap provides direct evidence of whether a port is open or closed.
- Security changes must be verified instead of assumed to have worked.
- Comparing scan results before and after hardening confirms whether exposure was actually reduced.
- Service hardening limits the number of network-accessible applications that an attacker can target.

## Workflow

### Test the HTTP Service with Telnet

Kali Linux connected directly to TCP port 80 on the Windows Server. An HTTP `HEAD / HTTP/1.0` request was sent through the active Telnet session to test the web service without requesting the full page body.

**Purpose**

- Confirm that TCP port 80 accepted connections.
- Verify that an HTTP service was actively responding.
- Identify the server software exposed through the service response.

**Result**

- The connection to `192.168.12.11:80` succeeded.
- Microsoft Internet Information Services 7.5 returned an `HTTP/1.1 404 Not Found` response.
- The response confirmed that the HTTP service was active even though the requested resource was not found.

### Disable the World Wide Web Publishing Service

The Windows Services console was opened on the Windows Server. The World Wide Web Publishing Service was selected, its startup type was changed to **Disabled**, and the running service was stopped.

**Purpose**

- Remove an unnecessary HTTP service from the network.
- Prevent the service from reopening TCP port 80 after a restart.
- Reduce the number of remotely reachable services on the server.

**Result**

- The first Nmap verification scan still reported TCP port 80 as open.
- The service configuration was checked again and corrected so the service was both stopped and disabled.

### Verify Port 80 with Nmap

Kali Linux scanned only TCP port 80 after the service state was corrected.

**Purpose**

- Confirm that the HTTP service was no longer listening.
- Validate the hardening change from an external system.
- Produce evidence that the exposed port had been closed.

**Result**

- Nmap reported `80/tcp closed http`.
- The Windows Server remained reachable, but no application was accepting connections on TCP port 80.

## Notes

### Complete Intended Lab Workflow

The complete lab guide included a broader service-discovery and hardening process than the minimum evidence required for the worksheet:

1. Run an initial Nmap TCP connect scan and review the detected services with Zenmap.
2. Test the Simple TCP/IP services on ports 7, 9, 13, 17, and 19 with Telnet.
3. Test File Transfer Protocol on port 21, Telnet on port 23, Simple Mail Transfer Protocol on port 25, and HTTP on port 80.
4. Disable Simple TCP/IP Services, Microsoft FTP Service, Telnet, Simple Mail Transfer Protocol, and World Wide Web Publishing Service on the Windows Server.
5. Rescan each affected port to verify that the services were no longer accessible.

### Interpreting the HTTP Response

The `404 Not Found` response did not indicate a failed connection. It showed that the HTTP request reached Microsoft Internet Information Services and that the server returned a valid HTTP response, confirming that the web service was listening on port 80.

### Troubleshooting Observations

- The HTTP `HEAD` request had to be entered while the Telnet connection was still active. Entering it after the Kali shell prompt returned would not test the remote web service.
- Changing a service's startup type to **Disabled** did not automatically prove that the running instance had stopped.
- When the first Nmap scan still showed port 80 as open, the correct response was to return to the service configuration, confirm that the service status was **Stopped**, and scan again.
- The final Nmap result, rather than the intended configuration, served as the authoritative verification.

## Commands Used

### Test the HTTP Service

```bash
telnet 192.168.12.11 80
HEAD / HTTP/1.0
echo "Connor Arnold"
```

### Open the Windows Services Console

```bash
services.msc
```

### Verify the Port State

The port-specific Nmap scan was run once after the initial service change and again after correcting the service state.

```bash
nmap 192.168.12.11 -p 80
nmap 192.168.12.11 -p 80
echo "Connor Arnold"
```

## Quick Reference

| Item | Purpose |
|------|---------|
| TCP port 80 | Default port used by unencrypted HTTP traffic |
| Telnet | Creates a plaintext connection to a remote TCP service |
| `HEAD / HTTP/1.0` | Requests HTTP response headers without downloading a full page body |
| Microsoft Internet Information Services | Microsoft web-server platform that responded on port 80 |
| World Wide Web Publishing Service | Windows service that provides Internet Information Services web connectivity |
| Nmap | Scans hosts to identify accessible ports and services |
| `open` | Indicates that an application is accepting connections on the port |
| `closed` | Indicates that the host responded but no application is listening on the port |
| Disabled startup type | Prevents a service from starting automatically |
| Stopped service status | Confirms that the current service process is no longer running |

## Related Playbook Pages

- [File Transfer Protocol (FTP)](../concepts/ftp-file-transfer-protocol.md) (coming soon)
- [HTTP](../concepts/http-hypertext-transfer-protocol.md)
- [Nmap](../tools/nmap.md)
- [Nmap Scan Reference](../tools/nmap-scan-reference.md)
- [Port Scanning](../concepts/port-scanning.md)
- [Ports and Port Numbers](../concepts/ports-and-port-numbers.md)
- [TCP/IP](../concepts/tcp-ip.md)
- [Telnet](../concepts/telnet.md) (coming soon)
