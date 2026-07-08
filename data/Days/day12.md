---
layout: default
title: Day 12
nav_order: 12
permalink: /day12
---

## 08/07/2026 [ Day 12: Locking Things Down with AppArmor ]

Today's topic: **Access Control Lists (ACLs)**, which give more fine-grained file permissions than the basic owner/group/everyone system from Day 3, plus a Linux security tool called **AppArmor**. AppArmor restricts exactly what each individual program is allowed to do -  which files it can touch, what network access it gets -  so that even if that program gets compromised, the damage stays boxed in rather than spreading across the whole system.

```
sudo apt update
sudo usermod -aG sudo username                                  # add a user to the sudo group
sudo apt install apparmor apparmor-utils apparmor-profiles
sudo systemctl status apparmor                                  # check it's actually running
sudo aa-status                                                  # see which profiles are currently active
sudo aa-genprof /usr/bin/firefox                                # generate a brand-new profile for an app
sudo aa-enforce /etc/apparmor.d/user.bin.firefox                # fully ENFORCE the profile -  blocks anything disallowed
sudo aa-complain /etc/apparmor.d/user.bin.firefox                # "complain mode" -  just LOGS violations instead of blocking, great for testing a new profile safely
sudo aa-disable /etc/apparmor.d/user.bin.firefox                # turn a profile off entirely
```

A couple of stray, unrelated notes from class, included only because they got mentioned: downloading a **Windows Server 2022 ISO** ahead of next week's Windows labs, and **Samba (smbd)** being the service that lets a Linux machine share files with Windows machines over SMB (the same port 445 from the Day 3 table).

(Two sketchier tool names also came up in passing in class. I'm leaving them out of this report entirely -  not something I'm going to document, even in a cleaned-up form, since they weren't really part of the actual structured lab work anyway.)