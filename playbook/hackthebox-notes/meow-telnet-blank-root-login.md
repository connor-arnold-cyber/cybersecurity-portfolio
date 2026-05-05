# Hack The Box - Meow

## Machine:
Meow

## Date:
05/05/2026

## Difficulty:
Very Easy

## Objective:
Connect to the target, confirm it is reachable, enumerate open services, identify a possible way to access the machine, and retrieve the flag.

## Target IP:
10.129.169.227

---

## Recon / Enumeration:
- Confirmed the target was reachable using `ping`.
- `ping` sends an ICMP Echo Request to a target. If the target replies, it confirms that my computer can communicate with the machine.
- The target responded successfully, which confirmed that my VPN connection was working and that the machine was online.
- Ran an Nmap scan to identify open ports and services.
- Nmap found one open TCP port: `23/tcp`.
- Port `23/tcp` was running Telnet.
- Nmap identified the service as `Linux telnetd`.
- Telnet is a remote login service that allows command-line access over the network.
- Telnet is insecure because it does not encrypt traffic.
- Since Telnet was the only open service, it became the next logical thing to test.

## Commands Used:
- `ping 10.129.169.227`
  - Tests whether the target is reachable over the network.
  - Uses ICMP Echo Request and Echo Reply.
  - In this lab, ping worked, proving the VPN and target connection were good.

- `nmap -sC -sV 10.129.169.227`
  - Scans the target for open ports and services.
  - `nmap` means Network Mapper. It checks what network “doors” are open.
  - `-sC` runs Nmap’s default scripts. These scripts collect extra useful information about services, banners, and common safe checks.
  - `-sV` detects service versions. This means it tries to identify what specific service or software is running behind an open port.
  - `10.129.169.227` is the target IP address.

## Nmap Result:
```text
23/tcp open telnet Linux telnetd
