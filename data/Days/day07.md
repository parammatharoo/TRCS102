---
layout: default
title: Day 07
nav_order: 7
permalink: /day07
---

## 01/07/2026 [ Day 7: Hunting Vulnerabilities ]

Today's big question: once you know a service is running and which version it is, how do you actually find out if it's breakable?

Every known vulnerability gets a **priority/severity rating** -  Low, Medium, High, Critical -  telling defenders how urgently it needs patching. (This gets a proper numeric score later, on Day 19, called CVSS.)

**Where vulnerabilities get catalogued and tracked:**
- **NVD** -  the National Vulnerability Database, the US government's official feed.
- **ExploitDB** -  a huge public archive of actual working exploit code.
- **Rapid7** -  the company behind Metasploit; they run their own vulnerability research and database too.
- **MITRE / CVE** -  CVE stands for Common Vulnerabilities and Exposures, and it's basically the official ID number every publicly known bug gets assigned (format: `CVE-YEAR-NUMBER`), maintained by MITRE.
- **GitHub** -  not an official database, but realistically where a ton of proof-of-concept exploit code actually ends up published first.

The general process: **disclosure** (someone responsibly reports the bug to the vendor, or irresponsibly just posts it) → **discovery** (you find the same weakness sitting on your target) → scan/grab the service's version banner → identify the exact software version → check that version against a vulnerability database.

**The "old-school" manual way:**
```
nmap ipaddress -p 21 -sV
```
Say this comes back reporting `vsftpd 2.3.4` is running on port 21. Now take that straight into Metasploit:
```
msf > search vsftpd 2.3.4
msf > set rhost ip_address
msf > set lhost your_ip
```
(`rhost` = the target you're attacking, `lhost` = your own machine, needed so the exploit knows where to send a connection back to.) If the module fires successfully, you land in a **meterpreter** session -  an interactive remote command shell running on the victim's machine, managed entirely through Metasploit. This particular `vsftpd 2.3.4` bug is a genuinely famous one, by the way -  a backdoor was maliciously planted in that exact version back in 2011, which is precisely why Metasploitable ships with it: it's a perfect, safe, legal teaching example.

**The "new-school" way, closer to how real researchers actually work:** search online for `"<software version> CVE"`, then take that CVE number straight to GitHub, where someone has almost always already published working (or semi-working) exploit code to study, adapt, or just learn from.


