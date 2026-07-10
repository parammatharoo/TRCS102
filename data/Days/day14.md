---
layout: default
title: Day 14
nav_order: 14
permalink: /day14
---

## 10/07/2026 [ Day 14: LDAP and Active Directory (Filling In the Gaps) ]

Missed this session, so this entry is filled in from the syllabus and classmates' notes rather than first-hand.

**Fact-check:** my scribbled note had the LDAP port written as 309 -  the real number is **389** (636 for the encrypted version, LDAPS). Corrected below.

**LDAP (Lightweight Directory Access Protocol)** -  the protocol used to look up and manage entries in a directory service: basically a giant structured phonebook of users, computers, groups, and permissions. Runs on **port 389** (plain, unencrypted) or **port 636** (LDAPS, encrypted).

**Active Directory (AD)** is Microsoft's implementation of this exact idea -  a centralized database that manages every user, computer, and permission across an entire company network. Setting up a domain controller:

**Server Manager → Add roles and features → (click through the wizard) → Active Directory Domain Services**

Once installed, that one server becomes the authoritative "brain" that every other Windows machine on the network checks in with for logins, group memberships, and permissions. This is also exactly why Active Directory is such a juicy target in real-world attacks -  compromise the domain controller and you've effectively compromised the whole company's Windows environment in one shot.


