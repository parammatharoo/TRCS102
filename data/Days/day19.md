---
layout: default
title: Day 19
nav_order: 19
permalink: /day19
---

## 20/07/2026 [ Day 19: Scanning for Weaknesses, Properly This Time ]

Going a level deeper into **vulnerability scanning**, this time with dedicated, purpose-built tools instead of manually chaining Nmap scans with Google searches:
- **Nessus**, **OpenVAS**, **Qualys** -  all automated vulnerability scanners. Point one at a target, and it runs through literally thousands of known checks automatically, then hands back a structured report ranked by severity (Low/Medium/High/Critical, the same scale from Day 7), typically scored using **CVSS** (Common Vulnerability Scoring System -  a standardized 0–10 number quantifying "how bad is this, really").

**The general vulnerability assessment process:** scope the target → scan it → analyze the results → prioritize which fixes matter most → write the report → re-check after fixes are applied to confirm they actually worked.

**Penetration testing phases** -  the bigger picture everything done across the whole month actually fits into:
1. **Reconnaissance** -  gathering information about the target (OSINT from Day 11, basic scanning).
2. **Scanning** -  actively finding open ports and running services (Nmap, RustScan from Days 3 and 5).
3. **Gaining Access / Exploitation** -  actually breaking in using a found weakness (Metasploit, Hydra, SQL injection, etc.).
4. **Maintaining Access** -  in a real engagement, this is where an attacker tries to keep their foothold (we've mostly stayed in the recon/scan/exploit stages so far, by design).
5. **Covering Tracks / Reporting** -  a real attacker hides evidence; a *pen tester* instead writes everything up clearly for the client.

And all of it conducted under **ethical hacking guidelines** -  written permission from the system's actual owner, a clearly defined scope of what's allowed to be tested, and responsibly reporting findings afterward instead of running off with them. The entire reason labs like Metasploitable and DVWA exist is so all of this can be practiced without needing anyone's real-world permission in the first place -  they're pre-approved punching bags.

