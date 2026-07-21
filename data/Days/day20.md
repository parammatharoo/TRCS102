---
layout: default
title: Day 20
nav_order: 20
permalink: /day20
---

## 21/07/2026 [ Day 20: Building Our Own Tool ]

Today we tried building a basic attack/defence tool ourselves, in Python, with an AI assisting along the way (used Claude for this part). Nothing fancy or production-grade -  just getting a genuine feel for how security tools actually get built under the hood, instead of only ever being a user of other people's finished tools.

Also carried out a **file inclusion attack** on DVWA, running inside Metasploitable:

**DVWA → Vulnerabilities → File Inclusion**, then inspecting and modifying the URL directly:
```
x.x.x.x/dvwa/vuln/fi/?page=include.php
```
If the application doesn't properly validate what file name gets passed through that `page` parameter, you can potentially make it load and display files from elsewhere entirely on the server's filesystem -  meaning an attacker could read local configuration files, source code, or logs they were never supposed to have access to. This is why "never trust user input, ever, even for something as innocent-looking as a filename" is basically rule zero of web security.

