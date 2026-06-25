---
layout: default
title: Day 04
nav_order: 4
permalink: /day04
---


## 25/06/2026 [ Day 4: Logs, Services, and the Humble `stat` ]

Today was Linux system-admin basics -  how to check what your machine has actually been up to, and who's been poking at it.

**Checking logs, the detective work:**
- `/var/log/auth.log` -  the history of logins, sudo usage, and authentication attempts. First place to look if you suspect someone's been fiddling with your login.
- `journalctl` -  the modern, unified way to read logs for the *entire* system, not just one file.
  - `journalctl -f` -  follow logs **live**, as they happen, scrolling in real time.
  - `journalctl -u servicename` -  logs for **one specific service only** (so you're not wading through everything else).
  - `sudo journalctl --since "30 minutes ago"` -  only show recent logs, which saves you from scrolling through a week of noise to find one incident.

**Controlling services** (a "service" is just a background program -  a web server, a database, SSH's own daemon, etc.):
```
sudo systemctl start servicename     # start it
sudo systemctl status servicename    # check if it's alive and healthy
systemctl enable servicename          # make it auto-start on every boot
sudo systemctl stop servicename       # stop it
```

**Networking quick check:**
```
ip a
```
Shows your network interfaces:
- `lo` -  loopback, your machine talking to itself (localhost, 127.0.0.1).
- `eth0` -  wired ethernet.
- `wlan0` -  Wi-Fi.

**Note worth tattooing on your brain:** SSH (remote login) runs on **port 22** by default -  this single fact will come up roughly every other day for the rest of the semester.

**Other handy commands collected today:**
- `head file` / `tail file` -  peek at just the first or last few lines of a file, instead of dumping the whole thing on screen.
- `deluser username` / `delgroup groupname` -  remove a user or a group entirely.
- `stat filename` -  shows metadata about a file: size, permissions, owner, and last-modified/accessed/changed timestamps. Great for quietly checking if a file's been touched recently without opening it.

