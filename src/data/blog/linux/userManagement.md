---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: User Management  
featured: false  
draft: false  
tags:
  - Linux  
  - User Management  
description: Understanding effective user management in Linux and the tools used for creating, modifying, and deleting user accounts, groups, and executing commands with elevated privileges.

---

**User Management**

Effective user management is a fundamental aspect of Linux system administration. Administrators frequently need to create new user accounts or assign existing users to specific groups to enforce appropriate access controls. Additionally, executing commands as a different user is often necessary for tasks that require different privileges. For example, certain groups may have exclusive permissions to view or modify specific files or directories, which is essential for maintaining system security and integrity. This capability allows us to gather more detailed information locally on the machine, which can be critically important for troubleshooting or auditing purposes.

For example, imagine a new employee named Alex joins your company and is provided with a Linux-based workstation to perform their tasks. As a system administrator, you need to create a user account for Alex and add them to the appropriate groups that grant access to necessary resources, such as project files or development tools. Additionally, there may be situations where Alex needs to execute commands with elevated privileges or as a different user to complete certain tasks.

### Execution as a user
```bash
$ cat /etc/shadow
cat: /etc/shadow: Permission denied
```
The `/etc/shadow` file is a critical system file that stores encrypted password information for all user accounts. For security reasons, it is readable and writable only by the root user to prevent unauthorized access to sensitive authentication data.

To perform tasks that require elevated privileges, users can utilize the `sudo` command. The `sudo` command, short for "superuser do," allows permitted users to execute commands with the security privileges of another user, typically the superuser or root. This enables users to perform administrative tasks without logging in as the root user, which is a best practice for maintaining system security. We will explore `sudo` permissions in greater detail in the Linux Security section.

### Execution as root
```bash
$ sudo cat /etc/shadow
root:<SNIP>:18395:0:99999:7:::
daemon:*:17737:0:99999:7:::
bin:*:17737:0:99999:7:::
<SNIP>
```

### User Management Command List

| Command  | Description                                               |
|----------|-----------------------------------------------------------|
| `sudo`   | Execute command as a different user.                      |
| `su`     | The `su` utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed. |
| `useradd`| Creates a new user or updates default new user information.|
| `userdel`| Deletes a user account and related files.                 |
| `usermod`| Modifies a user account.                                  |
| `addgroup`| Adds a group to the system.                               |
| `delgroup`| Removes a group from the system.                          |
| `passwd` | Changes user password.                                     |

Understanding how user accounts, permissions, and authentication mechanisms operate enables us to identify vulnerabilities, exploit misconfigurations, and assess the security posture of a system effectively. The most effective way to gain proficiency in user management is to practice using the individual commands along with their various options in a controlled environment.

Feel free to experiment with the various commands and explore their functionalities. It's important to let your creativity guide you in deciding what you want to achieve. By combining these user management tools with the knowledge you've gained from the previous sections, you'll realize how much you've already learned. Apply your understanding of the Linux system: create new user accounts, set up files and directories for these users, select files, read and filter specific elements, and redirect them to the files and directories of the new users you've created. Feel free to explore extensively. On your target system, there's nothing that can't be fixed, and even if something goes wrong, you have the ability to reset the target and start anew until you feel confident.

---
