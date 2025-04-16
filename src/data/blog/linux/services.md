---
author: Sonam Tenzin
pubDatetime: 2025-04-16T22:39:05+06:00
modDatetime: 2025-04-16T22:39:05+06:00
title: Service and Process Management
featured: false
draft: false
tags:
  - Linux
  - Services
  - Processes
description: Summary of Linux service and process management including systemd usage, signals, and background/foreground handling.
---

## Service and Process Management

Services (daemons) are background processes with no direct user interaction. They are classified into:

### 1. System Services
- Run at startup.
- Responsible for initializing system components.
- Comparable to essential car parts like engine/transmission.

### 2. User-Installed Services
- Installed by users to provide extra features (e.g., SSH, Apache).
- Like a car’s GPS or air conditioning.

Daemons often end with `d`, like `sshd`, `systemd`.

---

## Goals When Managing Services/Processes:
1. Start/Restart a service/process.
2. Stop a service/process.
3. Monitor the status of a service/process.
4. Enable/Disable service on boot.
5. Locate a running service/process.

---

## systemd and systemctl

- `systemd`: Modern init system; first process on boot (PID 1).
- `/proc/`: Virtual filesystem to access process info.

### Useful systemctl Commands:
```bash
systemctl start ssh         # Start SSH service
systemctl status ssh        # Check service status
systemctl enable ssh        # Enable SSH on boot
systemctl list-units --type=service  # List all active services
```

### Check running processes:
```bash
ps -aux | grep ssh
```

### View logs:
```bash
journalctl -u ssh.service --no-pager
```

---

## Process States:
- **Running**
- **Waiting** (waiting for events/resources)
- **Stopped**
- **Zombie** (terminated but still in process table)

---

## Killing Processes

- **Signals** are sent to control processes.
- View all signals:
```bash
kill -l
```

### Common Signals:
| Signal | Description |
|--------|-------------|
| 1 | SIGHUP - Terminal closed |
| 2 | SIGINT - Ctrl+C |
| 3 | SIGQUIT - Ctrl+D |
| 9 | SIGKILL - Force kill |
| 15 | SIGTERM - Terminate |
| 19 | SIGSTOP - Stop (unhandleable) |
| 20 | SIGTSTP - Ctrl+Z (Suspend) |

### Kill a process by PID:
```bash
kill -9 <PID>
```

---

## Backgrounding a Process

### Suspend current process:
```bash
[Ctrl + Z]   # Sends SIGTSTP
```

### View jobs:
```bash
jobs
```

### Resume in background:
```bash
bg
```

### Start directly in background:
```bash
ping -c 10 www.hackthebox.eu &
```

---

## Foreground a Process

### List jobs:
```bash
jobs
```

### Bring process to foreground:
```bash
fg <job_id>
```

---

## Running Multiple Commands

### Semicolon (`;`)
- Runs all commands regardless of previous result.
```bash
echo '1'; echo '2'; echo '3'
```

### Double AND (`&&`)
- Runs next command only if previous succeeded.
```bash
echo '1' && ls MISSING_FILE && echo '3'
```

### Pipe (`|`)
- Sends output of one command as input to the next.

---
