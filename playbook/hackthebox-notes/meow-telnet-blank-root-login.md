# Hack The Box - Meow

## Lab Info

### Platform:
Hack The Box

### Path / Series:
Starting Point

### Machine:
Meow

### Date:
05/05/2026

### Difficulty:
Very Easy

### Main Topic:
Telnet enumeration and blank root login

### Target IP:
10.129.169.227

### Objective:
Connect to the target machine, confirm it is reachable, identify exposed services, access the machine through the available remote login service, and capture the flag.

---

## Quick Summary

This lab focused on basic recon, service identification, and weak credential exposure. I connected to the Hack The Box VPN, verified the target was reachable, identified Telnet running on port 23, connected to the Telnet service, logged in as root with a blank password, found `flag.txt`, and submitted the flag successfully.

The main lesson from this lab is that exposed remote login services become serious risks when paired with weak or blank credentials.

---

## Setup / Connection Notes

- Connected to Hack The Box using OpenVPN.
- Pwnbox was unavailable because the free usage time had already been used.
- The target machine was started from the Meow machine page.
- The target IP changed after restarting the machine, so I used the current IP shown by Hack The Box.
- Windows required extra setup because Nmap and Telnet were not available by default.

---

## Recon / Enumeration

### What I Did:
- Verified that the target was reachable.
- Scanned the target to identify open ports and services.
- Found one open TCP port.

### Commands Used:
```cmd
ping 10.129.169.227
nmap -sC -sV 10.129.169.227
```
## Results:
Ping succeeded with 0% packet loss.

23/tcp open  telnet  Linux telnetd

## Screenshots: 

![meow2](screenshots/meow2.png)
![meow3](screenshots/meow3.png)
![Completion Proof](screenshots/meow-complete.png)
