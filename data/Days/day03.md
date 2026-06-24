---
layout: default
title: Day 03
nav_order: 3
permalink: /day03
---


## 24/06/2026 -  Day 3: Permissions, Tools, and Poking at Ports

**Linux file management & permissions.** Every single file in Linux has an owner, a group, and a set of permissions (read, write, execute) for the owner, the group, and everyone else. You check permissions with `ls -l`, and change them with `chmod`. Managing who exists at all is done with commands like `adduser`, `usermod`, and `addgroup`. Linux is, frankly, a control freak about who is allowed to touch what -  which is exactly the point.

**Meet the toolbox.** Three tools that are about to become permanent roommates for the rest of the semester:
- **iptables** -  the old-school, slightly terrifying Linux firewall that controls exactly what traffic is allowed in and out.
- **Nmap** -  the network mapper. Tells you what's open, closed, or hiding on a target machine. The single most-used tool in this entire course, easily.
- **Wireshark** -  a packet sniffer. Lets you literally watch network traffic fly by, packet by packet, like security CCTV for your network card.

**Common ports cheat sheet** -  this table is going to come up again and again for the rest of the month, so it earns a permanent home right here:

| Port | Service |
|------|---------|
| 21 | FTP (File Transfer Protocol) |
| 22 | SSH / SFTP |
| 23 | Telnet |
| 25 | SMTP (sending email) |
| 53 | DNS |
| 80 | HTTP |
| 139 | NetBIOS |
| 389 | LDAP |
| 443 | HTTPS |
| 445 | SMB |
| 587 | SMTP submission (the "secure-ish" email-sending port) |
| 2049 | NFS |
| 3306 | MySQL |
| 3389 | RDP (Remote Desktop) |
| 5432 | PostgreSQL |
| 5900 | VNC |

**Setting up Metasploitable.** This is a deliberately broken, intentionally vulnerable Linux VM -  basically a punching bag built by security people, for security people, so we have something legal to attack. We set it up in VirtualBox next to our Kali attacker machine so everything stays sealed inside our own little lab network, not anywhere near the real internet.

Scanning it with Nmap, starting small:
```
nmap ip_address -p 21,22
```
Scans just ports 21 and 22 on the target -  quick and quiet.

Then the "tell me everything" version:
```
nmap ip_address -p- -sV -O
```
- `-p-` scans **all 65,535 ports**, not just the common ones.
- `-sV` tries to fingerprint the exact **version** of whatever software is running on each open port.
- `-O` attempts to guess the target's **operating system** based on quirks in how it responds to network packets.

A port, once scanned, comes back as one of three states:
- **open** -  something's actively listening, you can connect.
- **closed** -  nothing's there; the target politely (or not) refuses the connection.
- **filtered** -  a firewall is sitting in the way, so Nmap genuinely can't tell if it's open or not. The network equivalent of someone not answering the door -  are they out, or just ignoring you?

Also poked around `ls /usr/share/nmap/scripts` -  a folder absolutely stuffed with ready-made Nmap scripts (NSE scripts) for deeper, more specific scans -  and `nmap --script-help script_name`, which prints out what a script actually does before you run it blind, e.g.:
```
nmap ip_address -p 22 --script=ssh2-enum-algos
```
This checks which encryption algorithms an SSH server supports, which can hint at how outdated (and therefore crackable) its configuration is.

Briefly looked at **enum4linux**, a tool that pulls information out of Windows/Samba machines -  usernames, shares, password policies -  all without needing a password first. Pure reconnaissance, no exploitation yet.

