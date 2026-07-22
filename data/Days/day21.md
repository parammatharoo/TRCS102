---
layout: default
title: Day 21
nav_order: 21
permalink: /day21
---

## 22/07/2026 [ Day 21: SQL Injection, Round One ]

Explored **SQL injection** on the DVWA lab -  attacking login forms, filters, and search boxes by sneaking SQL syntax into fields that looked like normal, innocent text input, tricking the backend database into running commands it was never meant to run (the classic example being a login form returning *every single row* in a user table instead of just checking one).

Also covered **Digital Forensics** from the syllabus -  the process of properly investigating a system after an incident has already happened:
- **Chain of custody** -  a fully documented trail proving evidence wasn't tampered with from the exact moment it was collected to the moment it's presented, whether that's to management or, in serious cases, an actual court. Break the chain of custody and the evidence can become legally worthless, no matter how solid it actually is.
- **Evidence collection** has to be careful and exact -  investigators work off a forensic *copy* of the data, never the original, so nothing gets accidentally altered in the process of investigating it.
- Common tools: **FTK Imager** (creates bit-for-bit forensic copies of drives) and **EnCase** (a full, industry-standard forensic investigation suite).


