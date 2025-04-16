---

author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: Package Management  
featured: false  
draft: false  
tags:
  - Linux  
  - Package Management  
description: Overview of package management in Linux, covering tools, installation, dependencies, and usage with APT, dpkg, and more.

---

**Package Management**

Whether working as a system administrator, maintaining our own Linux machines at home, or building/upgrading/maintaining our penetration testing distribution of choice, it is crucial to have a firm grasp on the available Linux package managers and the various ways to utilize them to install, update, or remove packages. Packages are archives that contain binaries of software, configuration files, information about dependencies, and keep track of updates and upgrades. 

The features that most package management systems provide are:
- Package downloading
- Dependency resolution
- A standard binary package format
- Common installation and configuration locations
- Additional system-related configuration and functionality
- Quality control

We can use many different package management systems that cover different types of files like ".deb", ".rpm", and others. The package management requirement is that the software to be installed is available as a corresponding package. Typically, this is created, offered, and maintained centrally under Linux distributions. In this way, the software is integrated directly into the system, and its various directories are distributed throughout the system.

The package management software retrieves the necessary changes for system installation from the package itself and then implements these changes to install the package successfully. If the package management software recognizes that additional packages are required for the proper functioning of the package that has not yet been installed, a dependency is included and either warns the administrator or tries to reload the missing software from a repository, for example, and install it in advance.

If an installed software has been deleted, the package management system then retakes the package's information, modifies it based on its configuration, and deletes files. There are different package management programs that we can use for this. Here is a list of examples of such programs:

| Command  | Description                                               |
|----------|-----------------------------------------------------------|
| `dpkg`   | The `dpkg` tool is used to install, build, remove, and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is aptitude. |
| `apt`    | Apt provides a high-level command-line interface for the package management system. |
| `aptitude` | Aptitude is an alternative to `apt` and is a high-level interface to the package manager. |
| `snap`   | Install, configure, refresh, and remove snap packages. Snaps enable the secure distribution of the latest apps and utilities for the cloud, servers, desktops, and the internet of things. |
| `gem`    | Gem is the front-end to RubyGems, the standard package manager for Ruby. |
| `pip`    | Pip is a Python package installer recommended for installing Python packages that are not available in the Debian archive. It can work with version control repositories (currently only Git, Mercurial, and Bazaar repositories), logs output extensively, and prevents partial installs by downloading all requirements before starting installation. |
| `git`    | Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals. |

It is highly recommended to set up a virtual machine (VM) locally to experiment with it. Let us experiment a bit in our local VM and extend it with a few additional packages. First, let us install git by using `apt`.

### Advanced Package Manager (APT)
Debian-based Linux distributions use the APT package manager. A package is an archive file containing multiple ".deb" files. The `dpkg` utility is used to install programs from the associated ".deb" file. APT makes updating and installing programs easier because many programs have dependencies. When installing a program from a standalone ".deb" file, we may run into dependency issues and need to download and install one or multiple additional packages. APT makes this easier and more efficient by packaging together all of the dependencies needed to install a program.

Each Linux distribution uses software repositories that are updated often. When we update a program or install a new one, the system queries these repositories for the desired package. Repositories can be labeled as stable, testing, or unstable. Most Linux distributions utilize the most stable or "main" repository. This can be checked by viewing the contents of the `/etc/apt/sources.list` file. 

Example repository list:
```bash
# parrot repository
# this file was automatically generated by parrot-mirror-selector
deb http://htb.deb.parrot.sh/parrot/ rolling main contrib non-free
deb http://htb.deb.parrot.sh/parrot/ rolling-security main contrib non-free
```

APT uses a database called the APT cache. This is used to provide information about packages installed on the system offline. We can search the APT cache, for example, to find all Impacket related packages:
```bash
$ apt-cache search impacket
impacket-scripts - Links to useful impacket scripts examples
python3-impacket - Python3 module to easily build and dissect network protocols
```

We can then view additional information about a package:
```bash
$ apt-cache show impacket-scripts
Package: impacket-scripts
Version: 1.4
Architecture: all
Maintainer: Kali Developers <devel@kali.org>
Depends: python3-impacket (>= 0.9.20)
Priority: optional
Section: misc
```

We can also list all installed packages:
```bash
$ apt list --installed
```

If missing packages are needed, we can search for and install them using the following command:
```bash
$ sudo apt install impacket-scripts -y
```

### Using Git to Download Tools
Now that we have git installed, we can use it to download useful tools from GitHub. One such project is called 'Nishang'. We will deal with and work with the project itself later. First, we need to navigate to the project's repository and copy the GitHub link before using git to download it.

Create a folder for the project and clone it:
```bash
$ mkdir ~/nishang/ && git clone https://github.com/samratashok/nishang.git
```

### DPKG
We can also download programs and tools from the repositories separately. In this example, we download 'strace' for Ubuntu 18.04 LTS.
```bash
$ wget http://archive.ubuntu.com/ubuntu/pool/main/s/strace/strace_4.21-1ubuntu1_amd64.deb
```

We can then install the downloaded package using `dpkg`:
```bash
$ sudo dpkg -i strace_4.21-1ubuntu1_amd64.deb
```

Test the installation:
```bash
$ strace -h
```