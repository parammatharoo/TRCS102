---
layout: default
title: Day 28
nav_order: 28
permalink: /day28
---

## 31/07/2026 [ Day 28: Threat Hunting, Hardening, and Wrap-Up ]

Last day of the lab -  went out properly on the defensive side of things, which felt right after spending most of the month being the attacker.

**Threat hunting** -  instead of passively waiting around for an alert to fire, actively going looking for signs an attacker is already quietly inside the network, using:
- **EDR** (Endpoint Detection and Response) -  monitors individual devices continuously for suspicious behaviour, not just known malware signatures.
- **SIEM** (Security Information and Event Management) -  collects and correlates logs from across an entire network into one central place, so patterns that would be invisible in any single log become obvious when viewed together.
- Investigating **Indicators of Compromise (IoCs)** -  odd file hashes, unexpected outbound connections to unfamiliar IPs, surprise new user accounts that nobody remembers creating -  essentially a detective's checklist for "something here doesn't add up."

**Hardening** -  the practice of closing off every unnecessary door *before* an attacker ever gets a chance to try the handle:
- **OS hardening** (both Linux and Windows) -  removing unused software, disabling unused services, keeping everything fully patched, enforcing tight permissions by default rather than loose ones.
- **Network hardening** -  VPNs for secure remote access instead of exposing services directly to the internet, firewalls configured tightly with default-deny (remember Day 5, not the "allow everything and hope" approach), and network segmentation so that one compromised machine can't freely reach every other machine on the network.

**Looking back on the whole month:** started out not entirely sure of the difference between a port and a protocol, and ended up scanning networks, cracking Wi-Fi handshakes, brute-forcing logins, injecting SQL, sniffing raw packets, writing IDS rules, and poking around mobile, IoT, and cloud security -  all safely contained inside a legal lab environment built specifically for exactly this kind of practice. The biggest actual takeaway, somewhat anticlimactically: most hacking isn't dramatic movie-style typing at double speed, it's mostly patience, methodical checklists, and knowing precisely which tool to reach for at each stage -  plus apparently a real talent for finding typos in your own class notes a month later.

