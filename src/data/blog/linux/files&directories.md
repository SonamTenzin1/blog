---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: File & Directories
featured: false  
draft: false  
tags:  
  - linux
  - file management
description: file and directory management in Linux. Discusses creating, moving, copying files, and directory structures.
---

## **Linux File & Directory Management Notes**

### **Creating Files and Directories**
- `touch <filename>`: Create an empty file  
  - Example: `touch info.txt`
- `mkdir <dirname>`: Create a new directory  
  - Example: `mkdir Storage`
- `mkdir -p <nested/dir/structure>`: Create nested directories  
  - Example: `mkdir -p Storage/local/user/documents`

**View Directory Tree:**
- `tree .`: Shows the directory structure starting from the current location  

---

### **Creating Files in Subdirectories**
- You can create files in nested directories using relative paths:
  - `touch ./Storage/local/user/userinfo.txt`

---

### **Moving and Renaming Files/Directories**
- `mv <source> <destination>`: Move or rename files or directories  
  - Rename file: `mv info.txt information.txt`  
  - Move files: `mv file1 file2 <directory>/`

---

### **Copying Files**
- `cp <source> <destination>`: Copy files  
  - Example: `cp Storage/readme.txt Storage/local/`

---

### **Final Structure Example (after operations)**
```bash
.
└── Storage
    ├── information.txt
    ├── local
    │   ├── readme.txt
    │   └── user
    │       ├── documents
    │       └── userinfo.txt
    └── readme.txt
```

---

### **Next Topics Teased**
- **Redirection** (manipulating command output/input)
- **Text editors** like `vim` and `nano` for interactive file editing

---

