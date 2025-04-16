---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: File Descriptors and Redirections
featured: false  
draft: false  
tags:  
  - Linux
  - File Descriptors
  - Redirections
description: Overview of file descriptors and redirections in Linux. Discusses standard input, output, error streams, and how to redirect them using various commands.
---

## **File Descriptors and Redirections**

### **What is a File Descriptor?**
- A **file descriptor (FD)** is a unique identifier for an open file, socket, or I/O resource maintained by the kernel in Unix/Linux systems.
- It functions like a "ticket" for accessing a resource (e.g., files, processes).
- In Linux:
  - **STDIN (0)**: Data stream for input.
  - **STDOUT (1)**: Data stream for standard output.
  - **STDERR (2)**: Data stream for standard error output.

---

### **STDIN, STDOUT, and STDERR Examples**

1. **STDIN and STDOUT Example**:  
   Running `cat` takes standard input and returns it as standard output.
   ```bash
   cat
   # Input: SOME INPUT (you press ENTER)
   # Output: SOME INPUT (displayed as STDOUT)
   ```

2. **STDOUT and STDERR Example**:
   Using the `find` command to search for a file, showing both STDOUT and STDERR (with errors displayed):
   ```bash
   find /etc/ -name shadow
   # Error: "Permission denied" will show as STDERR (FD 2).
   ```

---

### **Redirecting File Descriptors**

1. **Redirecting STDERR to /dev/null**:  
   To ignore error messages and only show STDOUT:
   ```bash
   find /etc/ -name shadow 2>/dev/null
   ```

2. **Redirect STDOUT to a File**:  
   Redirect standard output to a file (`results.txt`), while errors are discarded:
   ```bash
   find /etc/ -name shadow 2>/dev/null > results.txt
   ```

3. **Redirect STDOUT and STDERR to Separate Files**:  
   Redirect both standard output and standard error to different files:
   ```bash
   find /etc/ -name shadow 2> stderr.txt 1> stdout.txt
   ```

4. **Redirect STDIN**:  
   Use the `<` symbol to redirect input from a file (like `stdout.txt`):
   ```bash
   cat < stdout.txt
   ```

5. **Append STDOUT to a File**:  
   Use `>>` to append output to an existing file, instead of overwriting it:
   ```bash
   find /etc/ -name passwd >> stdout.txt 2>/dev/null
   ```

6. **Redirect STDIN Stream to a File**:  
   Use `<<` to add standard input via a stream and redirect it to a file (`stream.txt`):
   ```bash
   cat << EOF > stream.txt
   # Input stream until EOF
   EOF
   ```

---

### **Pipes and Combining Redirections**

1. **Using Pipes (|)**:  
   Redirect the STDOUT of one command to another command. For example, `find` results passed to `grep` for filtering:
   ```bash
   find /etc/ -name *.conf 2>/dev/null | grep systemd
   ```

2. **Using Pipes with Other Commands**:  
   Pipe the output from one command into another, e.g., using `wc -l` to count the results:
   ```bash
   find /etc/ -name *.conf 2>/dev/null | grep systemd | wc -l
   ```

---