---
layout: default
title: Day 01
nav_order: 1 
permalink: /day01
---

## 22/06/2026 [ Day 1: So It Begins ]

**What even is this subject.** Cybersecurity is the practice of protecting systems, networks, and data from digital attacks -  whether that attacker is a bored teenager, an organized crime group, or a government. It covers everything from "did you reuse the same password everywhere" to "is this nuclear power plant's control system internet-facing" (please say no).

**Threats vs. vulnerabilities vs. risk** -  the holy trinity of this entire subject, and the thing every exam question will try to trip you up on:
- A **vulnerability** is a weakness -  an unlocked window, outdated software, a password that's just "admin123."
- A **threat** is whoever or whatever might exploit that weakness -  a hacker, a virus, even a careless employee.
- **Risk** is the combination of the two: how likely is this threat to actually exploit this vulnerability, and how bad would it be if it did. No vulnerability, no risk, no matter how scary the threat sounds.

**Common attack types, the starter pack:**
- *Phishing* -  fake emails or messages designed to trick you into handing over passwords or clicking something nasty. The "your bank account has been suspended, click here immediately" classic.
- *DoS / DDoS (Denial of Service / Distributed Denial of Service)* -  flooding a server with so much traffic it gives up and stops responding to real users. DDoS is the same idea but coming from thousands of machines at once (usually a botnet), which is why it's so much harder to block.
- *APT (Advanced Persistent Threat)* -  not a smash-and-grab. This is a well-resourced attacker quietly living inside a network for months, slowly siphoning data without tripping any alarms. Think patient burglar, not window-smasher.
- *Malware* -  the umbrella term for any bad software: viruses, worms, trojans, ransomware, spyware, all of it.

**The CIA Triad** -  not the spy agency, the three pillars every single thing in this course is trying to either protect or attack:
- **Confidentiality** -  only the right people can read the data. (Encryption lives here.)
- **Integrity** -  nobody can sneakily change the data without it being noticed. (Hashing lives here.)
- **Availability** -  the system actually works and responds when someone legitimately needs it. (This is the one DDoS attacks go after.)

If you ever get stuck describing what an attack "does," you can almost always answer it in terms of which leg of this triangle it's kicking.