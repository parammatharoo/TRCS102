---
layout: default
title: Day 25
nav_order: 25
permalink: /day25
---

## 28/07/2026 [ Day 25: Mobile Security ]

Today's focus (from the syllabus): **mobile device security.**

- Both major mobile operating systems -  **Android** and **iOS** -  have their own distinct security models. Android apps run sandboxed and must request permissions for sensitive access; iOS is generally more locked-down by default, with Apple manually reviewing every app before it reaches the App Store.
- **Mobile app security testing** looks for issues like insecure local data storage on the device, weak or unauthenticated API calls back to a server, hardcoded passwords or API keys left sitting inside the app's compiled code, and apps requesting far broader permissions than they actually need to function.
- **Mobile penetration testing** applies the exact same reconnaissance → scanning → exploitation mindset from Day 19, just aimed at an app and the phone's OS instead of a traditional server.

Worth remembering: most real-world mobile "hacks" aren't flashy, movie-style zero-day exploits -  they're overwhelmingly just apps asking for way more access than they need, and users tapping "Allow" on autopilot without ever reading what they just agreed to.

