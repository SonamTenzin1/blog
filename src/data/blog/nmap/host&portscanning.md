---
author: Sonam Tenzin
pubDatetime: 2024-01-03T20:40:08Z
modDatetime: 2024-01-08T18:59:05Z
title: Host and Port Scanning with Nmap
featured: false
draft: false
tags:
  - nmap
description: Host and port scanning are crucial steps in penetration testing. Nmap is a powerful tool for this, offering various options for discovering hosts and services on a network. This guide covers how to use Nmap for host and port scanning, including techniques, options, and examples.
---

###  **Purpose of Scanning**
To gain a deeper understanding of a target system, after confirming it's online:
- **Open ports & services**
- **Service versions**
- **OS information**
- **Data shared by services**

---

###  **Port States in Nmap**
| State              | Description |
|-------------------|-------------|
| `open`            | Port actively accepts connections (e.g., TCP, UDP, SCTP). |
| `closed`          | Port is accessible but no service listening; RST received. |
| `filtered`        | No response or error; likely a firewall is in place. |
| `unfiltered`      | ACK scan shows the port is reachable, but state is unknown. |
| `openfiltered`   | No response; Nmap can't tell if open or filtered. |
| `closedfiltered` | Seen in IP ID idle scans; ambiguous due to lack of response. |
---

###   **Scanning Techniques**
#### **TCP SYN Scan (`-sS`)** *(Default if run as root)*
- Sends SYN packet → Waits for SYN-ACK (open) or RST (closed).
- Stealthy; doesn’t complete handshake.

#### **TCP Connect Scan (`-sT`)**
- Completes full TCP handshake (SYN → SYN-ACK → ACK).
- Accurate but **not stealthy** (logs generated).
- Good fallback when raw packet privileges aren’t available.

#### **UDP Scan (`-sU`)**
- Sends empty UDP datagrams.
- Open: rarely gets a response.
- Closed: ICMP Type 3, Code 3 (Port Unreachable).
- Slow due to no handshake.

---

### 📡 **Nmap Options Used**
| Option                | Description |
|-----------------------|-------------|
| `--top-ports=10`      | Scans top 10 most common ports. |
| `-p`                  | Specify port(s) (e.g., `-p 22,80`, `-p-`, `-p 1-1000`). |
| `-F`                  | Fast scan (top 100 ports). |
| `--packet-trace`      | Shows raw packets sent/received. |
| `-Pn`                 | Disables ICMP ping (assumes host is up). |
| `-n`                  | Disables DNS resolution. |
| `--disable-arp-ping`  | Skips ARP requests. |
| `--reason`            | Shows why Nmap assigned each port state. |

---

###  **Examples**
- **Top 10 TCP Ports:**  
  `sudo nmap 10.129.2.28 --top-ports=10`
  
- **Trace SYN Packet to Port 21:**  
  `sudo nmap 10.129.2.28 -p 21 --packet-trace -Pn -n --disable-arp-ping`
  
- **Connect Scan on 443:**  
  `sudo nmap 10.129.2.28 -p 443 --packet-trace --disable-arp-ping -Pn -n --reason -sT`

- **UDP Scan on Port 137:**  
  `sudo nmap 10.129.2.28 -sU -Pn -n --disable-arp-ping --packet-trace -p 137 --reason`

---

### **Firewall Behavior**
- **Dropped Packets (Silent):** Port shown as `filtered`.  
- **Rejected Packets (ICMP Unreachable):** Nmap gets Type 3, Code 3 response.

