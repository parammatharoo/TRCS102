---
layout: default
title: Day 15
nav_order: 15
permalink: /day15
---

## 13/07/2026 [ Day 15: Remote Desktop Setup (Filling In the Gaps) ]

Also missed this session -  filled in from the syllabus.

Enabling **Remote Desktop Protocol (RDP, port 3389)** on the Windows Server so it can be administered remotely without anyone needing to sit in front of it physically:

**Server Manager → Local Server → Remote Desktop → select which users are allowed to connect remotely**

Basic Windows admin tools worth knowing alongside this: **Process Monitor (Procmon)** -  watches file, registry, and process activity in real time, great for figuring out exactly what a program is doing under the hood, and **PsExec** -  lets you run commands on a remote Windows machine, conceptually similar to SSH for Linux (and, like SSH, a tool that's just as useful for attackers as it is for admins if credentials leak).

