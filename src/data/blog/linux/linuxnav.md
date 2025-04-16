---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: Linux Navigation
featured: false  
draft: false  
tags:  
  - Linux
  - Navigation
description: Linux navigation and file management notes. Discusses basic commands for navigating directories, listing files, and understanding file permissions. Provides examples and explanations for effective file management in Linux.
---

### **Linux Navigation and File Management Notes**

#### **Basic Navigation**
- `pwd`: Shows the current directory path.
- `ls`: Lists contents of a directory.
  - `ls -l`: Lists with detailed info (permissions, owner, size, etc.).
  - `ls -la`: Includes hidden files (starting with `.`).
  - `ls -l /path`: Lists contents of a specific directory without navigating there.

#### **Changing Directories**
- `cd <dir>`: Move to a directory.
- `cd /full/path`: Navigate directly using absolute path.
- `cd ..`: Move to the parent directory.
- `cd -`: Go back to the previous directory.

#### **Shortcuts and Tools**
- **Autocomplete**: Press `[TAB]` to autocomplete paths.
- **Dot Entries**:
  - `.` refers to the current directory.
  - `..` refers to the parent directory.
- `clear` or `[Ctrl] + [L]`: Clears the terminal screen.
- `[↑]` and `[↓]`: Scroll through command history.
- `[Ctrl] + [R]`: Reverse search command history.

#### **Example Directory Listing Output (from `ls -l`)**
| Column | Description |
|--------|-------------|
| `drwxr-xr-x` | File type and permissions |
| `2` | Number of hard links |
| `sonam` | File owner |
| `htbacademy` | Group owner |
| `4096` | File size or blocks used |
| `Nov 13 17:34` | Last modified date |
| `Desktop` | File or directory name |

---