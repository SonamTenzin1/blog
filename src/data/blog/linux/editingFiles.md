---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: Editing Files in Linux  
featured: false  
draft: false  
tags:  
  - Linux
  - Files
description: Overview of file editing in Linux using Nano and Vim editors. Discusses basic commands, shortcuts, and system files. 
---

## **Editing Files in Linux**

### **Nano Editor (Beginner-Friendly Text Editor)**

#### **Create/Edit a File:**
```bash
nano <filename>
```
- Example: `nano notes.txt`

#### **Nano Key Shortcuts**
- `^` means **CTRL**
- `CTRL + W`: Search  
- `CTRL + O`: Save (Write Out)  
- `CTRL + X`: Exit  
- `CTRL + K`: Cut Line  
- `CTRL + U`: Paste Line  
- `CTRL + C`: Show cursor position  

#### **Save and Exit Workflow**
1. After editing, press `CTRL + O` → Press `ENTER` to confirm filename.
2. Then press `CTRL + X` to exit.

#### **View File Content in Shell**
```bash
cat notes.txt
```

---

### **Important System Files to Know**
- `/etc/passwd`: Contains usernames, UIDs, GIDs, home directories.
- `/etc/shadow`: Contains password hashes (more secure).
- **Penetration testers** inspect these for misconfigured permissions.

---

## **Vim Editor (Advanced, Modal Editor)**

### **Start Vim:**
```bash
vim
```

### **Vim Modes (Key Concept)**
| Mode        | Purpose                                                                 |
|-------------|-------------------------------------------------------------------------|
| **Normal**  | Default mode for navigation and commands                                |
| **Insert**  | Type `i` to enter insert mode (to write text)                           |
| **Visual**  | Select text visually (`v` or `V`) for editing                           |
| **Command** | Accessed by `:` (e.g., `:w`, `:q`, `:wq`)                                |
| **Replace** | Use `R` to overwrite characters                                         |
| **Ex**      | Advanced scripting mode (less commonly used directly)                   |

### **Vim Basic Commands**
- `i`: Insert mode  
- `Esc`: Exit to normal mode  
- `:q`: Quit  
- `:w`: Save  
- `:wq`: Save and quit  
- `:q!`: Force quit without saving  

### **Practice Vim with Vimtutor**
```bash
vimtutor
```
- ~25–30 min tutorial
- Teaches core Vim commands interactively
- Highly recommended for beginners

---