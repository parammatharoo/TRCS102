---
layout: default
title: Day 27
nav_order: 27
permalink: /day27
---

## 30/07/2026 [ Day 27: Cloud Security ]

Today's focus: **cloud security**, from the syllabus.

- **Cloud service models:**
  - **IaaS** (Infrastructure as a Service) -  you rent raw virtual machines and storage; you're responsible for managing the OS and everything built on top of it.
  - **PaaS** (Platform as a Service) -  the provider manages the OS and runtime environment too; you just deploy your own code on top.
  - **SaaS** (Software as a Service) -  fully finished software you simply use (like Gmail); you manage essentially nothing underneath it at all.
- **Cloud security best practices:**
  - **IAM (Identity and Access Management)** -  carefully controlling exactly who, and what, can access each individual cloud resource, following the **principle of least privilege** (give the absolute minimum access actually needed, nothing extra "just in case").
  - **MFA (Multi-Factor Authentication)** -  requiring a second, separate proof of identity beyond just a password (an authenticator app code, a text message, a hardware key). One of the single simplest, highest-impact security measures that exists, full stop.

A huge proportion of real-world cloud data breaches ultimately come down to one single root cause: someone left a storage bucket, database, or admin panel publicly accessible by mistake, and nobody noticed until it was far too late.

