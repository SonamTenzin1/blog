---
author: Simon Smale
pubDatetime: 2024-01-03T20:40:08Z
modDatetime: 2024-01-08T18:59:05Z
title: Linux OS
featured: false
draft: false
tags:
  - Linux
description: Linux is an OS. It is a key tool in cybersecurity, known for being robust, flexible, and open-source. As an operating system, it manages computer hardware and enables software-hardware communication. Linux comes in different versions called distros.
---

# Linux

Linux is an OS. It is a key tool in cybersecurity, known for being robust, flexible, and open-source. As an operating system, it manages computer hardware and enables software-hardware communication. Linux comes in different versions called distros.

# Linux Philosophy

Everything is a file - Configuration files for Linux services are stored as text files.

Small, single-purpose programs - Linux provides modular tools that work together.

Program chaining - Tools can be combined for complex data processing tasks.

Shell-based interface - Linux primarily uses terminal commands for better system control.

Text-based configuration - System settings are stored in text files (e.g., /etc/passwd for user data).

# Linux Components

Bootloader- Code that starts the operating system. Parrot Linux uses GRUB.

OS Kernel- Core component managing hardware resources and I/O devices.

Daemons- Background services ensuring key functions like scheduling and printing work correctly. Load after boot or login.

OS Shell- Command line interface between OS and user. Common shells include Bash, Tcsh/Csh, Ksh, Zsh, and Fish.

Graphics server- "X" or "X-server" enables graphical programs to run locally or remotely.

Window Manager- GUI with options like GNOME, KDE, MATE. Provides file browsers and system management tools.

Utilities- Programs performing specific functions for users or other programs.

# Linux Architecture

Hardware- Physical components like RAM, hard drive, and CPU.

Kernel- Core system component that manages hardware resources and provides virtual resources to processes while preventing conflicts.

Shell- Command-line interface for users to execute kernel functions.

System Utility- Provides access to operating system functionality.

# File System Hierarchy

Linux follows the Filesystem Hierarchy Standard (FHS), organizing files in a tree structure with these main directories:

/ - Root directory containing all files needed for system boot and mounting other filesystems.

/bin - Essential commands
/boot - Boot files and kernel
/dev - Device files
/etc - System and app configs
/home - User directories
/lib - System libraries
/media - Removable devices
/mnt - Temporary mounts
/opt - Third-party tools
/root - Root user home
/sbin - System administration tools
/tmp - Temporary files
/usr - Programs and libraries
/var - Variable data files
