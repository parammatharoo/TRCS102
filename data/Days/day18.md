---
layout: default
title: Day 18
nav_order: 18
permalink: /day18
---

## 17/07/2026 [ Day 18: Honeypots and a Virus Scanner ]

**Fact-check:** my notes called this "inclusion detection system" -  the actual term is **Intrusion** Detection System. Related to, but not the same concept as, the file-inclusion attack we'd cover a few days later on Day 20 -  easy mix-up, fixing it here.

**Honeypots** -  decoy systems deliberately set up to *look* vulnerable, so attackers waste their time and effort poking at them instead of real production systems -  and so defenders get to quietly watch exactly how an attack unfolds, in a controlled way, without any real risk. Today's example was a **host-based honeypot** using a simple script:
```
honeyport/honeyport.py
```
This fakes an open, juicy-looking service on a port that has no legitimate reason to be touched -  when something connects to it, that's an immediate, high-confidence red flag that someone is poking around where they shouldn't be, since no normal user would ever have a reason to hit that port.

Also touched SSH server config:
```
sudo vim /etc/ssh/sshd_config
```
and `sudo systemctl status service` as a quick way to confirm exactly which config file a running service is actually using -  handy when you've edited a config and want to double check it's not silently reading from a different file somewhere else.

**VirusTotal** -  a free online tool that scans a file, photo, or hash against dozens of antivirus engines simultaneously (free tier handles files up to roughly 600MB) and reports back whether any of them flag it as malicious. One of the single most useful "is this safe" tools that exists, and it's free.


