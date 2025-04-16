---
author: Sonam Tenzin
pubDatetime: 2024-01-03T20:40:08Z
modDatetime: 2024-01-08T18:59:05Z
title: Host Discovery with Nmap
featured: false
draft: false
tags:
  - nmap
description: Host discovery is the first step in a penetration test. Nmap is a powerful tool for this, offering various options for discovering hosts on a network. This guide covers how to use Nmap for host discovery, including scanning entire networks, IP lists, and individual hosts.
---

### Internal Network Host Discovery with Nmap

When conducting an internal penetration test, the first step is to identify which systems are online. Nmap offers various host discovery options, with the most common being **ICMP echo requests**.

It’s recommended to **save every scan** for documentation and comparison, as different tools may yield different results.

---

### Scan an Entire Network Range
```bash
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```
- `-sn`: Disable port scan (ping only)  
- `-oA tnet`: Output in all formats  

This method depends on host firewalls. If ICMP is blocked, use evasion techniques.

---

### Scan from IP List
```bash
cat hosts.lst
sudo nmap -sn -oA tnet -iL hosts.lst | grep for | cut -d" " -f5
```
- `-iL`: Read IPs from file  
Only responding hosts will be shown. Others may be blocking ICMP.

---

### Scan Multiple or Ranged IPs
```bash
sudo nmap -sn -oA tnet 10.129.2.18 10.129.2.19 10.129.2.20
sudo nmap -sn -oA tnet 10.129.2.18-20
```

---

### Scan a Single IP
```bash
sudo nmap 10.129.2.18 -sn -oA host
```

To confirm it uses ICMP, add:
```bash
sudo nmap 10.129.2.18 -sn -oA host -PE --packet-trace
```

To see *why* Nmap marks a host as "up":
```bash
sudo nmap 10.129.2.18 -sn -oA host -PE --reason
```

To force ICMP (no ARP):
```bash
sudo nmap 10.129.2.18 -sn -oA host -PE --packet-trace --disable-arp-ping
```

---

By paying attention to Nmap's behavior (ICMP vs ARP), we can better understand host responses. More advanced discovery techniques can be used if ICMP is blocked.

--- 
