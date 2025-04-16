---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: Permission Management  
featured: false  
draft: false  
tags:
  - Linux  
  - Permissions  
  - Security  
description: This note covers the concepts of file permissions, ownership, and special permissions in Linux, including SUID, SGID, and Sticky bits.

---

**Permission Management**

In Linux, permissions control access to files and directories. These permissions are assigned to both users and groups, determining what actions—like reading, writing, or executing—are allowed. Permissions are a key element in ensuring proper security and collaboration within a Linux system.

### Types of Permissions:
- **(r)** - Read
- **(w)** - Write
- **(x)** - Execute

### Permission Representation
Permissions are represented in a specific format when listing files with the `ls -l` command. Here's an example:

```
-rwx rw- r-- 1 root root 1641 May 4 23:42 /etc/passwd
```

**Breaking it down:**
- **File type**: `-` means a regular file, `d` means a directory.
- **Permissions**: The three sections represent the owner's, group's, and others' permissions respectively.
- **Owner/Group**: The file's owner and group.
- **File size** and **date** are also displayed.

### Changing Permissions
Permissions can be changed using the `chmod` command, which can adjust permissions for the owner, group, or others. For example:

```
chmod a+r shell
```

This will add read permissions for all users.

### Octal Representation
Linux permissions can also be expressed using octal values, which are derived from binary values. Here’s how the calculation works:

- **Binary**: `rwx = 111`, `rw- = 110`, `r-- = 100`
- **Octal Value**: `7`, `6`, `4`

Thus, the octal value `754` translates to:
- Owner: `rwx` (7)
- Group: `r-x` (5)
- Others: `r--` (4)

### Changing Ownership
The `chown` command is used to change the owner and/or group of a file:

```
chown root:root shell
```

### Special Permissions: SUID, SGID, and Sticky Bit

#### **SUID (Set User ID)**
When the SUID bit is set on a file, the file is executed with the permissions of the file's owner, rather than the user running it. This can provide necessary elevated rights for certain applications.

#### **SGID (Set Group ID)**
The SGID bit works similarly to SUID, but the file is executed with the permissions of the file's group.

#### **Sticky Bit**
The sticky bit is set on a directory and ensures that only the file's owner, the directory's owner, or root can delete or rename files. It is typically used in shared directories where multiple users may have access to the same files.

```
drwxrwxrwt  3 cry0l1t3 cry0l1t3 4096 Jan 12 12:30 scripts
```

- A lowercase "t" means the sticky bit is set and users can execute files.
- An uppercase "T" means the sticky bit is set, but users lack execute permissions, meaning they cannot traverse the directory.

This permission system ensures proper security and management of resources in a multi-user environment.

---