---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: Prompt Description
featured: false  
draft: false  
tags:  
  - Prompt
description: Overview of the bash prompt in Linux, including its default format, PS1 variable, and customization options. Discusses the significance of the prompt in penetration testing and shell behavior on compromised systems. 
---
---

## Bash Prompt Basics (Linux Shell)

### Default Prompt Format
- The **bash prompt** is the line of text where you type commands.
- By default, it displays:
  ```
  <username>@<hostname><current working directory>$
  ```
  - `username`: Who you are
  - `hostname`: Name of the computer
  - `current working directory`: The folder you're working in
  - `$`: Indicates a regular (non-root) user

### Home Directory
- Represented by a tilde `~`
- Default directory after login:
  ```
  <username>@<hostname>[~]$
  ```

### Root User Prompt
- Changes `$` to `#` to indicate elevated privileges:
  ```
  root@hostname[/directory]#
  ```

---

## Understanding the PS1 Variable

- `PS1` defines how the command prompt appears.
- Customizing `PS1` allows you to:
  - Show username, hostname, and current directory
  - Include IP address, date/time, and success/failure status of the last command
  - Add colors and special characters
- Especially useful during penetration testing for keeping track of activity.

---

## Shell Behavior on Compromised Systems

- In some cases (e.g., reverse shells), only a minimal prompt like `$` or `#` is shown.
- This is often due to the PS1 variable not being configured properly.

---

## Customization Details

### Configuration File
- Located in: `~/.bashrc`
- Can be edited to set or change the PS1 prompt format

### Special Characters for PS1
| Symbol        | Description                              |
|---------------|------------------------------------------|
| `\u`          | Username                                 |
| `\h`          | Hostname (short)                         |
| `\H`          | Hostname (full)                          |
| `\w`          | Full path of the current directory       |
| `\d`          | Date (e.g., Mon Feb 6)                   |
| `\D{%Y-%m-%d}`| Date in YYYY-MM-DD format                |
| `\t`          | Time (24-hour HH:MM:SS)                  |
| `\T`          | Time (12-hour HH:MM:SS)                  |
| `\@`          | Time (AM/PM format)                      |
| `\j`          | Number of background jobs                |
| `\n`          | New line                                 |
| `\r`          | Carriage return                          |
| `\s`          | Name of the shell                        |

---

