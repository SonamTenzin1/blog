---
author: Sonam Tenzin
pubDatetime: 2024-01-03T20:40:08Z
modDatetime: 2024-01-08T18:59:05Z
title: Saving Results with Nmap
featured: false
draft: false
tags:
  - nmap
description: Saving scan results is crucial for documentation and analysis. Nmap offers various output formats, including normal, grepable, and XML. This guide covers how to save Nmap scan results effectively, including examples and conversion to HTML.
---

##  Saving Nmap Scan Results

###  Why Save Results?
Saving scan outputs helps in:
- Comparing different scan types
- Logging findings for documentation or reporting
- Creating readable formats for analysis or sharing

---

###  Output Formats

| Format       | Flag   | File Extension | Description |
|--------------|--------|----------------|-------------|
| **Normal**   | `-oN`  | `.nmap`         | Default human-readable output |
| **Grepable** | `-oG`  | `.gnmap`        | Useful for parsing with tools like `grep`, `awk`, or scripts |
| **XML**      | `-oX`  | `.xml`          | Structured output for automation or HTML conversion |
| **All**      | `-oA`  | `.nmap`, `.gnmap`, `.xml` | Saves in all three formats (prefix is filename) |

---

###  Example Command

```bash
sudo nmap 10.129.2.28 -p- -oA target
```

- Scans **all ports** on IP `10.129.2.28`
- Saves results as:
  - `target.nmap`
  - `target.gnmap`
  - `target.xml`

---

###  Sample Outputs

#### 🔹 Normal Output (`target.nmap`)
```nmap
# Nmap scan report
Host is up (0.053s latency).
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
80/tcp  open  http
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)
```

#### 🔹 Grepable Output (`target.gnmap`)
```gnmap
Host: 10.129.2.28 ()  Status: Up
Ports: 22/open/tcp//ssh///, 25/open/tcp//smtp///, 80/open/tcp//http///
```

#### 🔹 XML Output (`target.xml`)
```xml
<host>
  <address addr="10.129.2.28" addrtype="ipv4"/>
  <port protocol="tcp" portid="22">
    <state state="open" reason="syn-ack"/>
    <service name="ssh"/>
  </port>
  ...
</host>
```

---

###  Convert XML to HTML

#### Tool: `xsltproc`

```bash
xsltproc target.xml -o target.html
```

- Produces `target.html`, a clean HTML report
- Ideal for presenting results in reports or to non-technical teams
