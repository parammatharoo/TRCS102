---
layout: default
title: Day 24
nav_order: 24
permalink: /day24
---


## 27/07/2026 [ Day 24: Malware, Scanners, and Threat Intel ]

**Online malware scanners:**
- **VirusTotal** -  scans files, APKs, and hashes against dozens of antivirus engines at once (first met back on Day 18).
- **Hybrid Analysis** -  a similar concept to VirusTotal, with its own sandboxing behind the scenes.
- **Any.Run** -  a paid, fully interactive malware sandbox -  you can actually watch the malware "run" in a safe, isolated environment and see exactly what it does, step by step, rather than just getting a static verdict.

**Types of malware, the full rogue's gallery:** worms (self-spreading, no human interaction needed), cryptojackers (secretly mine cryptocurrency using your hardware and electricity bill), spyware (quietly watches what you do), trojans (disguised as something legitimate), fileless malware (runs entirely in memory, leaving barely a trace on disk -  much harder to detect with traditional antivirus), botnets (networks of hijacked machines controlled remotely, often used for exactly the DDoS attacks from Day 1), rootkits (bury themselves deep in the OS specifically to hide from detection), adware (shoves ads at you), and **ransomware** -  locks your files, or your entire computer, and demands payment to unlock them.

**Static vs dynamic analysis** (from the syllabus): static analysis examines malware *without ever running it* (reading its code, structure, and strings), while dynamic analysis actually runs it inside a safe, isolated sandbox and observes what it does live. Each catches things the other misses -  static analysis is safe but can be fooled by obfuscation, dynamic analysis sees real behaviour but malware can sometimes detect it's in a sandbox and behave differently on purpose.

**Threat intelligence sites:**
- **AbuseIPDB** -  check whether a given IP address has a history of abuse reports from other users.
- **Shodan.io** -  a search engine, but for internet-connected *devices* instead of web pages -  cameras, industrial control systems, random exposed servers. Genuinely a little unsettling the first time you use it and realize how much is just sitting there, unprotected, indexed and searchable.
- **MalwareBazaar** -  a free/paid repository of real, actual malware samples, intended for research purposes.
- **ThreatFox** -  shares threat indicators (malicious IPs, domains, file hashes) tied to known malicious campaigns.

Quick note on **Incident Response**: when something does go wrong for real, the generally accepted lifecycle is Preparation → Detection → Containment → Eradication → Recovery → Lessons Learned. Having this plan written down and rehearsed *before* an incident ever happens is the entire point of having an Incident Response Plan in the first place -  figuring it out for the first time mid-crisis is how a bad day becomes a catastrophic week.

