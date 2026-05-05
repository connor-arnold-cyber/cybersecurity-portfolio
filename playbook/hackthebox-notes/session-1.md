# Hack The Box - Meow: Telnet Blank Root Login

## Machine:
Meow

## Platform:
Hack The Box - Starting Point

## Date:
05/05/2026

## Difficulty:
Very Easy

## Main Topic:
Telnet enumeration, basic service discovery, and weak login credentials

## Objective:
Connect to the target machine, confirm that it is reachable, enumerate open services, identify a possible way to log in, and retrieve the flag from the system.

## Target IP:
10.129.169.227

---

# Summary

This lab introduced the basic workflow for connecting to a Hack The Box machine, checking if the machine is reachable, scanning it for open ports, identifying the exposed service, and using that service to gain access.

The target machine only had one open TCP port: port 23. Nmap identified port 23 as Telnet, which is an old remote login service. After connecting to Telnet, the machine allowed login with the username `root` and a blank password. Once logged in, I was placed directly into a root shell on the Linux machine. From there, I listed the files in the current directory and read the contents of `flag.txt`.

This lab showed how dangerous weak or blank credentials can be, especially when paired with an insecure remote access service like Telnet.

---

# Recon / Enumeration

## What I Did

I first tested whether the target machine was reachable using `ping`.

Then I scanned the target with Nmap to identify open ports and services.

## Findings

- Ping confirmed the target was reachable.
- Nmap found one open TCP port: `23/tcp`.
- Port 23 was running Telnet.
- The target operating system appeared to be Linux.
- Telnet allowed remote login to the machine.

---

# Commands Used

## Ping

```cmd
ping 10.129.169.227
