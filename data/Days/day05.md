---
layout: default
title: Day 05
nav_order: 5
permalink: /day05
---


## 29/06/2026 [ Day 5: Firewalls, Meet UFW ]

Quick refresher before the hands-on part -  networking runs on the **OSI model** (7 conceptual layers, from physical cables up to the actual application) and the simplified, more real-world **TCP/IP model** that sits underneath nearly everything we do. Both describe how data gets chopped up, addressed, sent, and reassembled as it travels from "I typed something" all the way down to electrical signals on a wire, and back up again on the other end. Routers connect separate networks together, switches connect devices *within* one network, and firewalls/IDS/IPS sit at the chokepoints deciding what traffic gets through and keeping an eye out for trouble.

Then onto actually configuring a firewall. There are two common options on Linux:
1. **UFW** (Uncomplicated Firewall) -  beginner-friendly, readable commands, does the job for 95% of situations.
2. **iptables** -  the much older, much more powerful, much less forgiving tool that UFW is actually just a friendly wrapper around underneath.

UFW commands collected today:
```
ufw status                                    # check current rules
ufw enable                                    # turn the firewall on
sudo ufw default deny incoming                # block everything by default, then open only what's needed
sudo ufw allow 22                             # allow SSH in (by port number or by name, "ssh" works too)
sudo ufw status numbered                      # show rules with index numbers, needed for deleting them
sudo ufw delete rule_number                   # delete one specific rule by its number
ufw allow from 192.168.162.0/24 to any port 22   # allow one specific subnet in, but only on port 22
ufw allow from 192.168.162.0/24               # allow that whole subnet in on every port (much more permissive)
ufw reset                                     # wipe every rule and start completely fresh
```

Default-deny-then-allow is the golden rule of firewalls in general: start by blocking everything, and open only the exact doors you actually need. Starting the other way round (allow everything, then try to remember to block the bad stuff) is how half of all real-world breaches happen.

**Bonus tool -  RustScan.** A much faster alternative to Nmap for the initial "what ports are even open" step, written in Rust (hence the name, and hence it being stupidly fast):
```
rustscan -a ip_address
```
And it plays nicely with Nmap too -  anything after `--` gets handed straight to Nmap as extra flags, so you get RustScan's speed *and* Nmap's detail:
```
rustscan -a ip_address -- -sV -O
```

