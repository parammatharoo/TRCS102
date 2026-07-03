---
layout: default
title: Day 09
nav_order: 9
permalink: /day09
---

## 03/07/2026 [ Day 9: Cracking Wi-Fi (and a Crash Course in Crypto) ]

**Cryptography basics first**, since it underpins wireless security too (and basically everything else in this course from here on):
- **Symmetric encryption** -  the same single key both locks and unlocks the data. Fast, but both sides need to somehow share that key safely beforehand, which is the hard part.
- **Asymmetric encryption** -  a public key locks it, and only the matching private key can unlock it. Slower, but solves the "how do we share the key safely" problem, since the public key is, well, public.
- Common algorithms: **AES** (symmetric -  used in everything from Wi-Fi to full-disk encryption), **RSA** (asymmetric -  used in things like TLS/HTTPS handshakes), **SHA-256** (not encryption at all, a one-way **hashing** algorithm used to verify data hasn't been tampered with, since you can't reverse a hash back into the original data).

**Then, the fun part -  Wi-Fi attacks.** Two main flavours: brute force (guess the password) and phishing (trick someone into just handing it over).

```
iwconfig                                                          # check wireless interfaces
sudo airmon-ng start wlan0                                        # put the adapter into "monitor mode" (listen to everything, not just traffic addressed to you)
sudo airodump-ng wlan0mon                                         # scan nearby networks
sudo airodump-ng --channel 11 --bssid bssid_id -w new wlan0mon    # capture traffic on one specific network only
sudo aircrack-ng -w wordlist new_04.cap                           # crack the captured handshake using a wordlist
```
The whole attack hinges on capturing the **WPA handshake** -  the brief exchange that happens when a device connects to the Wi-Fi network -  and then trying every password in a wordlist against it offline. No wordlist match, no cracked password; the password strength genuinely matters here.

Wordlists don't grow on trees, so two tools for building your own:
- **CUPP** (Common User Passwords Profiler, run with `cupp -i`) -  builds a targeted wordlist from personal info about a target (name, birthday, pet's name, etc.) -  a reminder that "password + birth year" is not the clever combination you think it is.
- **Crunch** -  generates wordlists from custom character sets and patterns, useful when you're brute-forcing something with a known format rather than guessing from personal details.

Fake access point attack:
```
sudo airbase-ng -e "fake" -c 6 wlan0
```
Spins up a rogue Wi-Fi network named "fake" on channel 6, hoping nearby devices connect to *you* instead of the real router -  the wireless version of a fake login page.

There's even a fully automated version of this entire process called **Wifiphisher**, which handles the fake AP *and* the phishing page that follows.

Worth remembering from the syllabus: **WPA3** is the current, much stronger Wi-Fi security standard (fixes several of WPA2's known weaknesses), and a "Rogue Access Point" is exactly the attack built above -  an unauthorized AP set up specifically to intercept traffic from unsuspecting devices.

