---
title: "Managing Btrfs Snapshots with Snapper"
date: 2024-12-13
tags:
  - Linux
  - Btrfs
  - Snapper
  - System Administration
  - Filesystem
categories:
  - Guides
  - Linux
  - Filesystem Tools
summary: "A detailed guide to using Snapper for managing Btrfs snapshots, including installation, configuration, and examples for snapshot creation, deletion, and comparison."
author: "TheTechMokey"
notes:
  - "Snapper integrates with Btrfs to provide robust snapshot management, leveraging features like copy-on-write."
  - "Includes information about the Btrfs Assistant GUI for easier management."
warnings:
  - "Ensure adequate disk space before creating numerous snapshots or enabling automated snapshots."
  - "Btrfs must be configured properly for Snapper to function effectively."
---


# Snapper
Website: http://snapper.io/
Github: https://github.com/openSUSE/snapper
[[Understanding Manpages]]: 
```
❯ man -k snapper  
dnf-snapper (8)      - DNF snapper Plugin  
snapper (8)          - Command-line program for filesystem snapshot management  
snapper-configs (5)  - Configuration files for snapper configs  
snapperd (8)         - DBus daemon for snapper
```

	Snapper is designed to work seamlessly with Btrfs, utilizing features like copy-on-write for snapshot creation. It offers granular control over snapshots, allowing for precise rollbacks to system states. Snapper also offers automated snapshot cleanup based on user defined policies to help you maintain your disk space.
## Install Snapper and it's necessary packages
```bash
sudo dnf install snapper dnf-plugin-snapper btrfs-assistant
```

| Package            | Purpose                                                                    |
| ------------------ | -------------------------------------------------------------------------- |
| snapper            | The primary snapshot management tool                                       |
| dnf-plugin-snapper | A DNF plugin that automatically creates snapshots before package upgrades  |
| btrfs-assistant    | A GUI tool for managing Snapper configurations and snapshots               |
				
## Create Snapper Config
```bash
sudo snapper create-config /
```
Creating this config in the `/` directory allows snapper to manage configs for the entire system

## Listing Snapshots
```bash
sudo snapper list
```

## Creating a New Snapshot
```bash
sudo snapper create --description "My System Configuration"
```

## Deleting a Snapshot
```bash
sudo snapper delete <ID>
```

## Reverting Changes to a Snapshot
```bash
sudo snapper revert <ID>
```

## Check difference between snapshots
```bash
snapper diff <ID> <ID>
```

# Btrfs Assisstant (GUI)

![[btrfs assistant.png]]

# Examples
## Example Installation
```bash
❯ sudo dnf install snapper dnf-plugin-snapper btrfs-assistant  
[sudo] password for mokey:    
Last metadata expiration check: 4:06:53 ago on Wed 25 Sep 2024 03:52:40 AM EDT.  
Dependencies resolved.  
=============================================================================================================================  
Package                                        Architecture        Version                       Repository            Size  
=============================================================================================================================  
Installing:  
btrfs-assistant                                x86_64              2.1.1-1.fc40                  updates              196 k  
python3-dnf-plugin-snapper                     noarch              4.1.2-1.fc40                  fedora                14 k  
snapper                                        x86_64              0.10.4-4.fc40                 fedora               500 k  
Installing dependencies:  
libbtrfs                                       x86_64              6.11-1.fc40                   updates               28 k  
libbtrfsutil                                   x86_64              6.11-1.fc40                   updates               33 k  
python3-dnf-plugins-extras-common              noarch              4.1.2-1.fc40                  fedora                47 k  
snapper-libs                                   x86_64              0.10.4-4.fc40                 fedora               349 k  
Installing weak dependencies:  
btrfsmaintenance                               noarch              0.5.2-1.fc40                  updates               31 k  
  
Transaction Summary  
=============================================================================================================================  
Install  8 Packages  
  
Total download size: 1.2 M  
Installed size: 3.4 M  
Is this ok [y/N]: y  
Downloading Packages:  
(1/8): libbtrfs-6.11-1.fc40.x86_64.rpm                                                       161 kB/s |  28 kB     00:00       
(2/8): python3-dnf-plugin-snapper-4.1.2-1.fc40.noarch.rpm                                     77 kB/s |  14 kB     00:00       
(3/8): btrfsmaintenance-0.5.2-1.fc40.noarch.rpm                                              147 kB/s |  31 kB     00:00       
(4/8): python3-dnf-plugins-extras-common-4.1.2-1.fc40.noarch.rpm                             214 kB/s |  47 kB     00:00       
(5/8): libbtrfsutil-6.11-1.fc40.x86_64.rpm                                                   146 kB/s |  33 kB     00:00       
(6/8): btrfs-assistant-2.1.1-1.fc40.x86_64.rpm                                               703 kB/s | 196 kB     00:00       
(7/8): snapper-0.10.4-4.fc40.x86_64.rpm                                                      1.6 MB/s | 500 kB     00:00       
(8/8): snapper-libs-0.10.4-4.fc40.x86_64.rpm                                                 931 kB/s | 349 kB     00:00       
-----------------------------------------------------------------------------------------------------------------------------  
Total                                                                                        934 kB/s | 1.2 MB     00:01        
Running transaction check  
Transaction check succeeded.  
Running transaction test  
Transaction test succeeded.  
Running transaction  
 Preparing        :                                                                                                     1/1    
 Installing       : libbtrfsutil-6.11-1.fc40.x86_64                                                                     1/8    
 Installing       : libbtrfs-6.11-1.fc40.x86_64                                                                         2/8    
 Running scriptlet: snapper-libs-0.10.4-4.fc40.x86_64                                                                   3/8    
 Installing       : snapper-libs-0.10.4-4.fc40.x86_64                                                                   3/8    
 Installing       : snapper-0.10.4-4.fc40.x86_64                                                                        4/8    
 Running scriptlet: snapper-0.10.4-4.fc40.x86_64                                                                        4/8    
 Installing       : btrfsmaintenance-0.5.2-1.fc40.noarch                                                                5/8    
 Running scriptlet: btrfsmaintenance-0.5.2-1.fc40.noarch                                                                5/8    
 Installing       : python3-dnf-plugins-extras-common-4.1.2-1.fc40.noarch                                               6/8    
 Installing       : python3-dnf-plugin-snapper-4.1.2-1.fc40.noarch                                                      7/8    
 Installing       : btrfs-assistant-2.1.1-1.fc40.x86_64                                                                 8/8    
 Running scriptlet: snapper-libs-0.10.4-4.fc40.x86_64                                                                   8/8    
 Running scriptlet: btrfs-assistant-2.1.1-1.fc40.x86_64                                                                 8/8    
  
Installed:  
 btrfs-assistant-2.1.1-1.fc40.x86_64                       btrfsmaintenance-0.5.2-1.fc40.noarch                               
 libbtrfs-6.11-1.fc40.x86_64                               libbtrfsutil-6.11-1.fc40.x86_64                                    
 python3-dnf-plugin-snapper-4.1.2-1.fc40.noarch            python3-dnf-plugins-extras-common-4.1.2-1.fc40.noarch              
 snapper-0.10.4-4.fc40.x86_64                              snapper-libs-0.10.4-4.fc40.x86_64                                  
  
Complete!
```

## Example Use
```bash
❯ sudo snapper create-config /  
❯ sudo snapper list  
# | Type   | Pre # | Date | User | Cleanup | Description | Userdata  
---+--------+-------+------+------+---------+-------------+---------  
0  | single |       |      | root |         | current     |            
❯ sudo snapper create --description "1_Sys_Conf"  
❯ sudo snapper list  
# | Type   | Pre # | Date                            | User | Cleanup | Description | Userdata  
---+--------+-------+---------------------------------+------+---------+-------------+---------  
0  | single |       |                                 | root |         | current     |            
1  | single |       | Wed 25 Sep 2024 08:00:32 AM EDT | root |         | 1_Sys_Conf  |
```

## Example Diff
### Output Example
```
❯ snapper diff 0..1     
--- /root/.dbus/session-bus/13b3ee8f8d9d4d71b50fb4a4f30c82f6-0  2024-09-25 08:01:09.033447873 -0400  
+++ /.snapshots/1/snapshot/root/.dbus/session-bus/13b3ee8f8d9d4d71b50fb4a4f30c82f6-0    2024-09-23 21:41:25.523224997 -0400  
@@ -3,6 +3,6 @@  
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will  
# be used rather than this file.  
# See "man dbus-launch" for more details.  
-DBUS_SESSION_BUS_ADDRESS='unix:path=/tmp/dbus-NgUwI6oqxJ,guid=c73c49a1804fd07b8613df8066f3fb85'  
-DBUS_SESSION_BUS_PID=47199  
+DBUS_SESSION_BUS_ADDRESS='unix:path=/tmp/dbus-EjfhAZoX02,guid=8ffef216e4ae090f1a92ac6a66f218c5'  
+DBUS_SESSION_BUS_PID=38149  
DBUS_SESSION_BUS_WINDOWID=20971521  
--- /var/lib/chrony/drift       2024-09-25 08:04:26.527609626 -0400  
+++ /.snapshots/1/snapshot/var/lib/chrony/drift 2024-09-25 06:46:44.405090865 -0400  
@@ -1 +1 @@  
-           -5.868911             0.060714  
+           -5.850524             0.062922  
Binary files /var/lib/PackageKit/transactions.db and /.snapshots/1/snapshot/var/lib/PackageKit/transactions.db differ  
--- /var/lib/rsyslog/imjournal.state    2024-09-25 08:19:14.830892749 -0400  
+++ /.snapshots/1/snapshot/var/lib/rsyslog/imjournal.state      2024-09-25 07:59:59.085036423 -0400  
@@ -1 +1 @@  
-s=8acfe20534eb45a38076a6a555a474df;i=fe1d8;b=f6063cee01b643819a4f4a3ca13d5d08;m=5d1d9cec7;t=622f0a154a0f9;x=6e7c38db7bb67001  
\ No newline at end of file  
+s=8acfe20534eb45a38076a6a555a474df;i=fe016;b=f6063cee01b643819a4f4a3ca13d5d08;m=58cfa3888;t=622f05c750abb;x=d9aa16906e011e27  
\ No newline at end of file  
--- /var/log/audit/audit.log    2024-09-25 08:19:40.945048059 -0400  
+++ /.snapshots/1/snapshot/var/log/audit/audit.log      2024-09-25 08:00:32.607233610 -0400
...OUTPUT OMITTED...
```
#### Notice and the --- / +++
```bash
--- /root/.dbus/session-bus/13b3ee8f8d9d4d71b50fb4a4f30c82f6-0  2024-09-25 08:01:09.033447873 -0400  
+++ /.snapshots/1/snapshot/root/.dbus/session-bus/13b3ee8f8d9d4d71b50fb4a4f30c82f6-0    2024-09-23 21:41:25.523224997 -0400  
```