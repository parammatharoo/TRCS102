---
layout: default
title: Day 13
nav_order: 13
permalink: /day13
---

## 09/07/2026 [ Day 13: Into Windows Territory ]

Switched gears to Windows today, setting up a static IP address the old-fashioned GUI way:

**Control Panel → Network & Internet → Network Sharing Center → Change adapter settings → Ethernet properties → IPv4 properties**, then manually setting a fixed IP, subnet mask, and default gateway, plus a DNS server (`8.8.8.8` -  Google's public DNS, used here purely as a working example, not because it's mandatory).

Once the Windows Server had a fixed IP, we went straight back to Kali and scanned it with Nmap exactly like any Linux target -  a good reminder that Windows machines show up on a network scan the same as anything else; the OS behind an IP address doesn't make it invisible.

From the syllabus, worth remembering as background: Windows security fundamentals include checking **user privileges** (who's an admin vs. a standard user), the **Registry** (the enormous hierarchical settings database that basically the entire OS runs on), and **Event Logs** (Windows' equivalent of `journalctl` from Day 4 -  tracks logins, errors, and system events, viewable through the Event Viewer GUI).


