---
layout: default
title: Day 11
nav_order: 11
permalink: /day11
---

## 07/07/2026 [ Day 11: NFS, VNC, and a Dash of OSINT ]

**NFS (Network File System)** -  lets you mount a remote folder over the network so it behaves exactly like a local drive, running on **port 2049**. The classic bug: it's extremely common to see NFS set up with **no username or password at all**, just straight network-level access -  meaning anyone on the network can mount and browse it.

```
showmount -e ip_address                     # see what folders are being shared ("exported")
nmap ipaddress -p 2049 -sV                  # check if NFS is running on the target at all
mkdir /mnt/name                             # create an empty local folder to mount into
sudo mount -t nfs ipaddress:/ /mnt/class    # mount the remote share onto that local folder
```

**VNC (Virtual Network Computing)** -  full remote desktop access, running on **port 5900**. If the VNC password is weak (and it often is), Metasploit has modules that can brute-force it, after which you can connect directly:
```
vncviewer ip_address
```

**A peek into OSINT** (Open-Source Intelligence -  gathering information from entirely public sources, no hacking or exploitation required at all):
- **exiftool** -  pulls the hidden metadata out of a file, especially photos: camera make/model, GPS coordinates, timestamps, even the software used to edit it. A genuinely good reminder to strip metadata before posting photos publicly -  plenty of real-world location leaks have come from exactly this.


