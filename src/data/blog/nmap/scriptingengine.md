---
author: Sonam Tenzin
pubDatetime: 2024-01-03T20:40:08Z
modDatetime: 2024-01-08T18:59:05Z
title: Scripting Engine 
featured: false
draft: false
tags:
  - nmap
description: Scripting Engine 
---

### **Nmap Scripting Engine (NSE) Summary**

- **Purpose:** Automates advanced scanning tasks using Lua scripts.
- **Script Categories (14 total):**
  - `auth`: Checks authentication credentials.
  - `broadcast`: Discovers hosts via broadcast.
  - `brute`: Brute-forces credentials.
  - `default`: Default scripts used with `-sC`.
  - `discovery`: Finds accessible services.
  - `dos`: Checks for DoS vulnerabilities (use cautiously).
  - `exploit`: Attempts known exploits.
  - `external`: Uses external services.
  - `fuzzer`: Sends malformed input to test handling.
  - `intrusive`: May affect the target system.
  - `malware`: Detects malware.
  - `safe`: Non-intrusive scripts.
  - `version`: Enhances version detection.
  - `vuln`: Detects known vulnerabilities.

---

### **How to Use NSE Scripts:**

- **Default Scripts:**  
  `nmap <target> -sC`

- **Category-Based Scan:**  
  `nmap <target> --script <category>`

- **Specific Scripts:**  
  `nmap <target> --script <script1>,<script2>`

---

### **Examples:**

- **SMTP Script Usage:**
  ```bash
  nmap 10.129.2.28 -p 25 --script banner,smtp-commands
  ```
  - Reveals SMTP banner & available commands.

- **Aggressive Scan:**
  ```bash
  nmap 10.129.2.28 -p 80 -A
  ```
  - Performs service/version detection, OS fingerprinting, traceroute, and runs default scripts.

- **Vulnerability Scan with NSE:**
  ```bash
  nmap 10.129.2.28 -p 80 -sV --script vuln
  ```
  - Detects web app paths, WordPress versions, users, and known CVEs.

---

### **More Info:**  
NSE Script Reference: [https://nmap.org/nsedoc/](https://nmap.org/nsedoc/)

---

Let me know if you want a flashcard-style version or need help remembering key flags!