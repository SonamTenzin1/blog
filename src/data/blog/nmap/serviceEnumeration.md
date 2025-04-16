---
author: Sonam Tenzin
pubDatetime: 2024-01-03T20:40:08Z
modDatetime: 2024-01-08T18:59:05Z
title: Service Enumeration with Nmap
featured: false
draft: false
tags:
  - nmap
description: Service enumeration is a critical step in penetration testing. This guide covers how to use Nmap for service enumeration, including version detection and banner grabbing techniques.
---

### **Service Enumeration with Nmap**

- **Purpose:** Detect services and their versions to find potential vulnerabilities or exact exploits for specific versions.
  
- **Steps:**
  1. **Initial Quick Scan:** Start with a limited port scan to avoid detection.
  2. **Full Port Scan + Version Detection:**  
     `nmap -p- -sV [target]`  
     Scans all ports and detects service versions.
  
- **Options:**
  - `--stats-every=5s`: Show scan progress every 5 seconds.
  - `-v` / `-vv`: Increase verbosity to show open ports immediately.
  - `-Pn`: Skip host discovery (treat all hosts as up).
  - `-n`: Disable DNS resolution.
  - `--disable-arp-ping`: Avoid ARP pinging.
  - `--packet-trace`: Show sent/received packets during the scan.

- **Banner Grabbing:**
  - Nmap reads banners after connecting; sometimes they reveal more info than shown in the scan.
  - Manual tools like `nc` (netcat) and `tcpdump` can be used to grab full banners and observe TCP handshakes (including PSH-ACK packets with banner data).

- **Example Services Detected:**
  - OpenSSH, Apache, Postfix, Dovecot, etc.
  - Banners can include OS info like “Ubuntu.”
