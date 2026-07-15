---
layout: default
title: Day 17
nav_order: 17
permalink: /day17
---

## 15/07/2026 [ Day 17: Burp Suite Meets DVWA ]

Opened **Burp Suite** (an intercepting proxy -  it sits between your browser and a website, letting you see and modify every request and response that passes through) against **DVWA -  Damn Vulnerable Web Application** (login: `admin` / `password`, which is almost too on-the-nose for a *deliberately* insecure app). DVWA exists purely for practicing web attacks safely and legally.

Setup steps:
1. Start Burp's proxy and point the browser at it.
2. In the browser, go to `http://burpsuite/`, click **CA Certificate**, and import it under the browser's certificate settings -  this lets Burp decrypt and inspect HTTPS traffic too, not just plain HTTP. Without this step, Burp is blind to anything encrypted.

**Command injection practice on DVWA:** the app has a "ping this IP" feature that shows the raw command output inside a `<pre>` tag. Normal, intended use:
```
ip = 8.8.8.8 & submit = submit
```
But if the app doesn't properly filter what's typed into that field, you can chain on an *extra* command using a shell operator:
```
ip = 8.8.8.8 / whoami & submit = submit
```
and the server happily runs `whoami` too, printing its output right there in the response alongside the ping results. This is the entire idea behind a **command injection** vulnerability -  the application trusts user input way more than it should, and passes it straight to the underlying operating system's shell.

Also found **PortSwigger Web Security Academy** -  genuinely excellent, completely free, hands-on labs for practicing exactly this kind of web attack legally and in a structured way, way beyond what DVWA alone covers.

