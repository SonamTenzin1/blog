---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: System Information Gathering in Linux
featured: false  
draft: false  
tags:  
  - Linux 
description: System information gathering in Linux is crucial for understanding system architecture, installed software, and network configurations. This guide covers essential commands and tools for effective system information gathering in Linux environments.
---
## **Hands-On Linux Practice & System Information Gathering**

### Key Takeaways:
- You can always use `-h`, `--help`, or `man` to understand a command.
- These tools are essential for working with Linux, especially during security assessments, vulnerability hunting, and system hardening.

---

## Essential Linux Commands for System Information

| Command     | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `whoami`    | Shows the current username.                                                 |
| `id`        | Displays user ID, group ID, and group memberships.                          |
| `hostname`  | Prints the name of the host machine.                                        |
| `uname`     | Prints kernel and system-related info. Use flags like `-a`, `-r`, `-s`.     |
| `pwd`       | Prints the current working directory.                                       |
| `ifconfig`  | Views or sets IP address and interface details (older but still used).      |
| `ip`        | Modern replacement for ifconfig; manages IPs, interfaces, and routes.       |
| `netstat`   | Displays network connections, routing tables, interface stats, etc.         |
| `ss`        | More modern and faster version of `netstat` for socket stats.               |
| `ps`        | Shows current running processes.                                            |
| `who`       | Shows which users are logged in.                                            |
| `env`       | Prints current environment variables.                                       |
| `lsblk`     | Lists block storage devices.                                                |
| `lsusb`     | Lists USB devices connected to the system.                                  |
| `lsof`      | Lists open files and associated processes.                                  |
| `lspci`     | Lists PCI devices in the system.                                            |

---

## Logging in via SSH

SSH allows remote access to a system via the command line.

**Command to connect:**
```
ssh htb-student@[IP_address]
```

Used throughout exercises to access remote lab environments.

---

## Practical Examples

### `hostname`
Prints the system's hostname.
```
hostname
```
Output:
```
nixfund
```

---

### `whoami`
Prints the currently logged-in user.
```
whoami
```
Output:
```
cry0l1t3
```

---

### `id`
Shows UID, GID, and group memberships.
```
id
```
Example output:
```
uid=1000(cry0l1t3) gid=1000(cry0l1t3) groups=1000(cry0l1t3),1337(hackthebox),4(adm),24(cdrom)
```
Useful for:
- Identifying special group access (`sudo`, `adm`, etc.)
- Recognizing potential privilege escalation paths

---

### `uname`
Displays system and kernel information.

**Common options:**

| Option | Description                     |
|--------|---------------------------------|
| `-a`   | All available system info       |
| `-r`   | Kernel release                  |
| `-s`   | Kernel name                     |
| `-n`   | Hostname (nodename)             |
| `-v`   | Kernel version                  |
| `-m`   | Machine hardware name           |
| `-o`   | Operating system                |

Example:
```
uname -a
```
Output:
```
Linux box 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

To get just the kernel release:
```
uname -r
```

This can help you search for kernel-specific vulnerabilities:
> Example search: `4.15.0-99-generic exploit`

---
