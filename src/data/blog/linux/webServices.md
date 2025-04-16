---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05Z  
modDatetime: 2025-04-16T18:59:05Z  
title: Network Services  
featured: false  
draft: false  
tags:  
  - Network  
  - Security  
  - SSH  
  - NFS  
  - Web Server  
  - VPN  
description: Overview of network services including SSH, NFS, Web Servers, and VPNs. Discusses installation, configuration, and use cases for penetration testing and network administration.  
---

# Network Services

When working with Linux, managing various network services is essential. Proficiency in handling these services is crucial for several reasons. Network services are designed to perform specific tasks, many of which enable remote operations. It is important to have the knowledge and skills to communicate with other computers over the network, establish connections, transfer files, analyze network traffic, and configure these services effectively. This expertise allows us to identify potential vulnerabilities during penetration testing. Additionally, understanding the configuration options of each service enhances our overall comprehension of network security.

Consider a scenario where we are conducting a penetration test and encounter a Linux host being assessed for vulnerabilities. By monitoring network traffic, we observe that a user on this Linux host is connecting to another server via an unencrypted FTP server. Consequently, we are able to capture the user's credentials in plain text. This situation would be much less likely if the user were aware that FTP does not encrypt connections or the data transmitted. For a Linux administrator, this represents a critical oversight, as it not only exposes security weaknesses within the network but also reflects poorly on the administrators responsible for maintaining the network's security.

While it is not feasible to cover every network service, we will focus on the most important ones. This approach is beneficial not only for administrators and users, but also for penetration testers who need to understand the interactions between different hosts and their own systems.

## SSH

**Secure Shell (SSH)** is a network protocol that allows the secure transmission of data and commands over a network. It is widely used to securely manage remote systems and securely access remote systems to execute commands or transfer files. In order to connect to our or a remote Linux host via SSH, a corresponding SSH server must be available and running.

The most commonly used SSH server is the **OpenSSH server**. OpenSSH is a free and open-source implementation of the Secure Shell (SSH) protocol that allows the secure transmission of data and commands over a network. Administrators use OpenSSH to securely manage remote systems by establishing an encrypted connection to a remote host. With OpenSSH, administrators can execute commands on remote systems, securely transfer files, and establish a secure remote connection without the transmission of data and commands being intercepted by third parties.

### Install OpenSSH

```bash
sudo apt install openssh-server -y
```

### Check if the server is running

```bash
systemctl status ssh
```

### SSH - Logging In

```bash
ssh cry0l1t3@10.129.17.122
```

To configure OpenSSH, edit the configuration file `/etc/ssh/sshd_config`. This file allows us to adjust settings such as the maximum number of concurrent connections, the use of passwords or keys for logins, host key checking, and more.

## NFS

**Network File System (NFS)** is a network protocol that allows us to store and manage files on remote systems as if they were stored on the local system. It enables easy and efficient management of files across networks. For example, administrators use NFS to store and manage files centrally (for Linux and Windows systems) to enable easy collaboration and management of data.

NFS can also be used to share and manage resources efficiently. It supports features such as access controls, real-time file transfer, and simultaneous access by multiple users.

### Install NFS

```bash
sudo apt install nfs-kernel-server -y
```

### Check if the server is running

```bash
systemctl status nfs-kernel-server
```

### Create NFS Share

```bash
mkdir nfs_sharing
echo '/home/cry0l1t3/nfs_sharing hostname(rw,sync,no_root_squash)' >> /etc/exports
```

To mount an NFS share:

```bash
mkdir ~/target_nfs
mount 10.129.12.17:/home/john/dev_scripts ~/target_nfs
```

## Web Server

Understanding the operation of **web servers** is essential for penetration testers, as these servers are integral to web applications and frequently serve as primary targets during security assessments. A web server is software that delivers data, documents, applications, and various functions over the Internet. It utilizes the Hypertext Transfer Protocol (HTTP) to transmit data to clients such as web browsers and to receive requests from these clients.

### Install Apache Web Server

```bash
sudo apt install apache2 -y
```

### Configure Apache

```bash
<Directory /var/www/html>
  Options Indexes FollowSymLinks
  AllowOverride All
  Require all granted
</Directory>
```

## VPN

A **Virtual Private Network (VPN)** functions like a secure, invisible tunnel that connects us to another network, allowing seamless and protected access as if we were physically present within it. This is achieved by establishing an encrypted tunnel between the client and the server, ensuring that all data transmitted through this connection remains confidential and safeguarded from unauthorized access.

### Install OpenVPN

```bash
sudo apt install openvpn -y
```

### Connect to VPN

```bash
sudo openvpn --config internal.ovpn
```