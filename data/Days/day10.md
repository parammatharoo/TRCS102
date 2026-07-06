---
layout: default
title: Day 10
nav_order: 10
permalink: /day10
---

## 06/07/2026 [ Day 10: Setting a Trap with Snort ]

Today's tool: **Snort**, an open-source **Intrusion Detection System (IDS)** -  it passively watches network traffic and raises alerts when something matches a known-bad pattern, based on rules either written by the community or by you. Works fine inside a VirtualBox lab setup, or on real hardware if the switch supports port mirroring so Snort can actually see everyone else's traffic.

Config file lives at:
```
sudo nano /etc/snort/snort.lua
```
Inside, set `HOME_NET` to your actual network's IP range so Snort knows which traffic is "ours" to protect versus just background internet noise.

Enabling rules and alert formats:
```
enable_builtin_rules = true
include = 'rules/local.rules'

alert_csv = {file = true}
alert_fast = {file = true}
alert_json = {file = true}
```

Sanity-check the config file isn't broken before trusting it:
```
sudo snort -T -c /etc/snort/snort.lua
```
(`grep include` on the output is a quick way to spot a config error buried in a wall of text.)

Run it for real:
```
sudo snort -c /etc/snort/snort.lua -i eth0 -l /var/log/snort
```
- `-c` -  which config file to use.
- `-i` -  which network adapter to listen on.
- `-l` -  where to save the logs.

Writing detection rules completely by hand is painful and easy to get wrong syntax-wise, so -  no shame in admitting it -  asked an AI assistant directly: *"write a Snort IDS rule to detect ICMP packets in a network,"* then dropped the generated rule into:
```
sudo nano /etc/snort/rules/local.rules
```
(Always worth double-checking AI-generated security rules against the official Snort rule syntax before trusting them in anything beyond a lab -  a malformed rule can silently fail to match anything at all.)

Watch alerts come in live:
```
sudo tail -f /var/log/alert_fast.txt
```

Also got a mention of **Fail2ban** -  a tool that watches log files for repeated failed login attempts and automatically bans the offending IP at the firewall level. This is the actual answer to one of my Day 6 doubts about stopping brute force -  worth setting up properly in a future lab.

