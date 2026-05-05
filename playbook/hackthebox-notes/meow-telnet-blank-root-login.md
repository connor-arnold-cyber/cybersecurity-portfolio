# Hack The Box - Meow

## Lab Info
- Platform: Hack The Box
- Path / Series: Starting Point
- Machine: Meow
- Date: 05/05/2026
- Difficulty: Very Easy
- Main Topic: Telnet enumeration and blank root login
- Target IP: 10.129.169.227
- Objective: Identify the exposed service, access the machine, and capture the flag.

---

## Quick Summary
Completed the Meow machine on Hack The Box. I confirmed the target was reachable, identified Telnet running on port 23, logged in as `root` with a blank password, found `flag.txt`, and submitted the flag successfully.

Main lesson: exposed remote login services are risky when weak or blank credentials are allowed.

---

## Setup / Connection Notes
- Connected to HTB using OpenVPN.
- Pwnbox was unavailable due to the free usage limit.
- Windows needed extra setup because Nmap and Telnet were not available by default.
- The target IP changed after restarting the machine, so I used the current HTB-provided IP.

---

## Recon / Enumeration
### What I Did
- Used `ping` to confirm the target was reachable.
- Used Nmap to identify open ports and services.
- Found Telnet running on port `23/tcp`.

### Commands Used
```cmd
ping 10.129.169.227
nmap -sC -sV 10.129.169.227
```

## Screenshots: 

![meow2](screenshots/meow2.png)
![meow3](screenshots/meow3.png)
![Completion Proof](screenshots/meow-complete.png)
