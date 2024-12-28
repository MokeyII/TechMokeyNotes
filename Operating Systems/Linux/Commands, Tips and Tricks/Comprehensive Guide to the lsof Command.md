---
title: "Comprehensive Guide to the lsof Command"
date: 2024-09-26
tags:
  - Linux
  - lsof
  - Command-Line Tools
  - System Administration
categories:
  - Guides
  - Linux
  - Tools
summary: "A detailed guide to using the `lsof` command for inspecting open files, processes, and network connections in Linux."
author: "TheTechMokey"
notes:
  - "`lsof` is a versatile tool for listing open files and their associated processes, making it invaluable for debugging and system monitoring."
  - "Includes examples for filtering by user, PID, and protocol."
sources:
  - "man lsof"
warnings:
  - "Some `lsof` commands require root privileges to access system-wide file and process details."
  - "Output may vary based on system configuration and installed `lsof` version."
---


*CREATED: 09-26-00:43 EST*
*MANPAGE*: `man lsof`

---
# List of Open Files
## Description
Lsof revision 4.98.0 lists on its standard output file information about files opened by processes for the following UNIX dialects:  
- Apple Darwin 9, Mac OS X 10, macOS 11 and above  
- FreeBSD 8.2 and above  
- Linux 2.1.72 and above  
- NetBSD 1.2 and above  
- Solaris 9, 10 and 11 and above
# Files
## View Open Files
```bash
sudo lsof
```
## Finding open files by users
```bash
sudo lsof -u <username>
```
### example
```bash
❯ sudo lsof -u mokey  
lsof: WARNING: can't stat() fuse.portal file system /run/user/1000/doc  
     Output information may be incomplete.  
COMMAND     PID  USER   FD      TYPE             DEVICE  SIZE/OFF       NODE NAME
... OUTPUT OMITTED ...
Web\x20Co 80262 mokey   24r      REG                0,1      6842     157294 /memfd:mozilla-ipc (deleted)  
Web\x20Co 80262 mokey   25u     sock                0,9       0t0    6404212 protocol: UNIX-STREAM  
Web\x20Co 80262 mokey   26r      REG                0,1    872144     179216 /memfd:mozilla-ipc (deleted)
... OUTPUT OMITTED ...
```
## Finding open files by PID
```bash
lsof -p <PID>
```
### example
```bash
❯ lsof -p 80262  
COMMAND     PID  USER   FD      TYPE             DEVICE SIZE/OFF    NODE NAME  
Web\x20Co 80262 mokey  cwd       DIR               0,23        0 6399340 /proc/80267/fdinfo  
Web\x20Co 80262 mokey  rtd       DIR               0,23        0 6399340 /proc/80267/fdinfo  
Web\x20Co 80262 mokey  txt       REG               0,35   554048  362909 /usr/lib64/firefox/firefox
... OUTPUT OMITTED ...
```

# Network

## All TCP/UDP connections
```bash
sudo lsof -i
```
### Example
```bash
❯ sudo lsof -i  
[sudo] password for mokey:    
COMMAND     PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME  
systemd-r  1167 systemd-resolve   10u  IPv4    5987      0t0  UDP *:llmnr    
systemd-r  1167 systemd-resolve   11u  IPv4    5988      0t0  TCP *:llmnr (LISTEN)  
systemd-r  1167 systemd-resolve   12u  IPv6    5995      0t0  UDP *:llmnr    
systemd-r  1167 systemd-resolve   13u  IPv6    5996      0t0  TCP *:llmnr (LISTEN)  
systemd-r  1167 systemd-resolve   17u  IPv4    6000      0t0  UDP _localdnsstub:domain    
systemd-r  1167 systemd-resolve   18u  IPv4    6001      0t0  TCP _localdnsstub:domain (LISTEN)  
systemd-r  1167 systemd-resolve   19u  IPv4    6002      0t0  UDP _localdnsproxy:domain
... OUTPUT OMITTED ...
```
## Filter Specific Protocols
### All tcp
```bash
sudo lsof -i tcp
```
### All udp
```bash
sudo lsof -i udp
```
### All ipv4 tcp
```bash
sudo lsof -i 4tcp
```
### All ipv6 tcp
```bash
sudo lsof -i 6tcp
```
### TCP ipv4 @ domain
```bash
sudo lsof -i 4tcp@example.com
```

#### examples
```bash
❯ sudo lsof -i tcp  
  
COMMAND     PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME  
systemd-r  1167 systemd-resolve   11u  IPv4    5988      0t0  TCP *:llmnr (LISTEN)  
systemd-r  1167 systemd-resolve   13u  IPv6    5996      0t0  TCP *:llmnr (LISTEN)
... OUTPUT OMITTED ...
```
```bash
❯ sudo lsof -i udp  
COMMAND     PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME  
systemd-r  1167 systemd-resolve   10u  IPv4    5987      0t0  UDP *:llmnr    
systemd-r  1167 systemd-resolve   12u  IPv6    5995      0t0  UDP *:llmnr
... OUTPUT OMITTED ...
```
```bash
❯ sudo lsof -i 4tcp  
COMMAND     PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME  
systemd-r  1167 systemd-resolve   11u  IPv4    5988      0t0  TCP *:llmnr (LISTEN)  
systemd-r  1167 systemd-resolve   18u  IPv4    6001      0t0  TCP _localdnsstub:domain (LISTEN)  
... OUTPUT OMITTED ...
```
```bash
❯ sudo lsof -i 6tcp  
COMMAND     PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME  
systemd-r  1167 systemd-resolve   13u  IPv6    5996      0t0  TCP *:llmnr (LISTEN)  
cupsd      1546            root    7u  IPv6   27891      0t0  TCP localhost:ipp (LISTEN)
	```
