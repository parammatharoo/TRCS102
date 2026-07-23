---
layout: default
title: Day 22
nav_order: 22
permalink: /day22
---

## 23/07/2026 [ Day 22: SQLMap and Google-Fu ]

**SQLMap** -  automates the entire SQL injection process end-to-end, instead of crafting each payload by hand:
```
sqlmap -r file.txt --batch -dbs
```
- `-r file.txt` -  feeds it a captured HTTP request from a file (usually exported straight out of Burp Suite from Day 17).
- `--batch` -  auto-answers any interactive prompts instead of pausing to wait on you.
- `-dbs` -  lists every database it manages to find on the target.

**Google dorking** -  using Google's own advanced search operators to dig up things that probably shouldn't be publicly indexed in the first place:
```
site:example.com      -> only results from one specific site
filetype:pdf           -> only PDF files
ext:mkv                 -> only files with that exact extension
intitle:"admin"         -> pages with "admin" literally in the page title
inurl:"admin"           -> pages with "admin" literally in the URL
```
None of this counts as "hacking" in any technical sense -  it's entirely public search results -  but it's a genuinely eye-opening demonstration of how much sensitive stuff ends up publicly indexed purely because nobody configured access controls properly on their end.

Also found the **Wayback Machine** -  a massive archive of old snapshots of websites, basically a time machine for the internet, handy for seeing what a site used to look like (or used to expose) before it got fixed, taken down, or quietly patched.

