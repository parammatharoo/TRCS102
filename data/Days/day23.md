---
layout: default
title: Day 23
nav_order: 23
permalink: /day23
---

## 24/07/2026 [ Day 23: The OWASP Top 10 ]

Covered the **OWASP Top 10** -  the ten most common and most dangerous web application vulnerability categories, essentially the "greatest hits" list every serious web app gets tested against:

1. **Broken Access Control** -  users can access things they shouldn't (e.g. just changing `/account/232` to `/account/523` in the URL and suddenly seeing someone else's private data, because the server never actually checked whose account you're allowed to view).
2. **Cryptographic Failures** -  weak, missing, or misconfigured encryption exposing sensitive data in transit or at rest.
3. **Injection** -  SQL injection, command injection, and their many relatives (plenty of hands-on practice with this one already, see Days 15, 21, and 22).
4. **Insecure Design** -  security flaws baked into the application's fundamental design itself, not just a one-off coding mistake that can be patched.
5. **Security Misconfiguration** -  default passwords left unchanged, cloud storage buckets left open, unnecessary features or debug modes left switched on in production.
6. **Vulnerable and Outdated Components** -  using old libraries, frameworks, or software versions with known, publicly documented vulnerabilities (exactly the vsftpd 2.3.4 situation from Day 7).
7. **Identification and Authentication Failures** -  weak login systems, poor session handling, missing MFA.
8. **Software and Data Integrity Failures** -  trusting updates, plugins, or data from sources that were never properly verified or signed.
9. **Security Logging and Monitoring Failures** -  not noticing an attack is actively happening because nobody's actually watching the logs (the Snort/Fail2ban problem from Day 10, from the other direction).
10. **Server-Side Request Forgery (SSRF)** -  tricking a server into making network requests on the attacker's behalf, often reaching internal systems that would otherwise be unreachable from outside.

Also got a long, genuinely useful list of legal practice platforms to explore outside of class: **TryHackMe**, **Hack The Box**, **PortSwigger Academy**, **LetsDefend.io**, **Cybrary**, **Root Me**, **VulnHub**.

