---
layout: default
title: Day 08
nav_order: 8
permalink: /day08
---

## 02/07/2026 [ Day 8: Watching the Wire with Wireshark ]

Spent the start of the session re-scanning the FTP service (port 21) on Metasploit again -  repetition is apparently the whole curriculum here -  but the real focus today was **Wireshark**: a tool that captures and displays every single packet moving across a network interface, in real time, in enormous detail. Think of it as putting a microscope directly on your network card.

Two filters worth remembering:
```
ip.addr == 192.168.1.81
```
Shows every packet going **to or from** that IP -  both directions at once, the full conversation.

```
ip.src == 192.168.1.81
```
Shows **only** packets **sent from** that IP -  handy for isolating exactly what one specific machine is broadcasting onto the network, with none of the replies cluttering the view.

Wireshark on an unencrypted connection (plain HTTP, FTP, Telnet) is genuinely a little alarming the first time you use it -  usernames and passwords can show up sitting right there in plain text. It's a very fast, very visual argument for why HTTPS exists.



