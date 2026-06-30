---
layout: default
title: Day 06
nav_order: 6
permalink: /day06
---

## 30/06/2026 [ Day 6: Brute Force o'Clock ]

**Fact-check:** my original scribbled title for today said "attack ddos," but everything we actually did was **brute-forcing** login credentials -  which is a completely different attack from a DDoS. DDoS is about drowning a server in traffic until it can't respond to anyone (an *availability* attack, straight out of the CIA triad from Day 1). Brute-forcing is about guessing a password through sheer repetition (a *confidentiality* attack -  you're trying to get in, not knock the door down). Renaming today's entry accordingly so future-me doesn't get these mixed up on an exam.

Setup: **Kali Linux** as the attacker machine, aimed at our usual Metasploitable victim VM.

**Hydra** -  the classic, no-frills brute-force tool. Point it at a service, hand it a list of usernames and a list of passwords, and it just... tries all of them:
```
hydra -L userlist -P passwordlist ftp://192.168.1.1
```
- `-L` -  a **list** of usernames to try.
- `-P` -  a **list** of passwords to try.
- `-t 6` -  run 6 attempts at once (6 "threads"). Faster, but louder and easier for the target to notice.

**Fact-check:** the protocol needs that `ftp://` written in full in front of the target IP -  without it, Hydra won't know which service to speak to.

**Metasploit Framework (`msfconsole`)** -  does similar brute-forcing, but as one tiny slice of a much bigger toolkit, organized into "modules." Today's flavour of module: **auxiliary**, used for scanning, information-gathering, and non-exploit tasks like login brute-forcing.

```
msf > search ssh_login            # find a matching module
msf > use <number>                 # select the one you want
msf > info -d                      # read its full documentation
msf > show options                 # see every setting the module needs
msf > set rhost target_ip          # set the target (remote host)
msf > set user_file wordlist.txt   # set the username list
msf > set pass_file passwords.txt  # set the password list
msf > set verbose true             # print extra detail while it runs
msf > run                          # launch the attack
msf > sessions                     # see any sessions we gained access to
msf > session -i session_number    # jump into a specific one
```

**My doubts from today, now actually answered:**
- *How would a victim even know a brute-force attack is happening?* Mostly through logs -  `/var/log/auth.log` (or `journalctl -u sshd`, remember Day 4) fills up with repeated failed login attempts from the same source, usually in a tight burst. A monitoring tool or IDS (hi, Snort, we'll meet you properly on Day 10) would flag the sudden spike automatically instead of someone having to notice it by eye.
- *What can a victim actually do to stop or slow it down?* Account lockouts after N failed attempts, rate-limiting login attempts, enforcing strong passwords so the wordlist stops working, enabling MFA so a correct password alone isn't enough, and tools like **Fail2ban** (mentioned again on Day 10) which auto-bans an IP after repeated failures.
- *This doesn't show us the attacker's real IP - how would a defender trace that back?* In our lab, the "attacker" IP is right there in the logs because we're on the same local network with no obfuscation. In the real world, attackers hide behind VPNs, proxy chains, Tor, or botnets of already-compromised machines, so tracing the *true* source usually needs cooperation from ISPs, law enforcement, and sometimes international legal processes - which is exactly why so many real attacks never get definitively attributed.

