---
title: "Understanding and Using the lsblk Command in Linux"
date: 2024-10-04
tags:
  - Linux
  - lsblk
  - Command-Line Tools
  - System Administration
categories:
  - Guides
  - Linux
  - Tools
summary: "A detailed guide to the `lsblk` command in Linux, covering its usage, options, and outputs for analyzing block devices and file systems."
author: "TheTechMokey"
notes:
  - "`lsblk` is a versatile tool for listing block devices and their attributes, such as file systems, mount points, and more."
  - "Includes JSON output options for scripting and automation."
sources:
  - "https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/"
warnings:
  - "Some advanced options or detailed outputs may require root privileges."
  - "Be cautious when modifying block devices to avoid data loss."
---


*Source:* https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/
Date Created: 10/4/2024
# What is `lsblk`
lsblk lists information about all available or the specified block devices. The lsblk  command reads the sysfs filesystem and udev db to gather information. If the udev db is not  available or lsblk is compiled without udev support, then it tries to read LABELs, UUIDs  and filesystem types from the block device. In this case root permissions are necessary.

For a deeper look into the file systems on your block devices, use the `-f` flag:
```bash
lsblk -f
```
This will display not just the block devices, but also details about the file systems on each partition, including the type (e.g., ext4, vfat, swap), the UUID, and the current mount points.

```bash
❯ lsblk -f  
NAME        FSTYPE FSVER LABEL       UUID                                 FSAVAIL FSUSE% MOUNTPOINTS  
sda                                                                                         
└─sda1      vfat   FAT32 PORTABLE_WD C9B2-[....]                                              
zram0                                                                                    [SWAP]  
nvme1n1                                                                                     
├─nvme1n1p1 vfat   FAT32             3[...]                             579.8M          3% /boot/efi  
├─nvme1n1p2 ext4   1.0               73734ea3-[....]                    445.6M         47% /boot  
└─nvme1n1p3 btrfs        fedora      e5e3bda2-[....]                    1.4T           24% /home  
                                                                                        /  
nvme0n1                                                                                     
└─nvme0n1p1 btrfs        fedora      e5e3abcd-[....]
```

If you want less information about the devices themselves (without showing partitions or mount points), the `-d` option is useful:
```bash
lsblk -d  
```
```sh
❯ lsblk -d  
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS  
sda       8:0    0 465.8G  0 disk    
zram0   252:0    0     8G  0 disk [SWAP]  
nvme1n1 259:0    0 931.5G  0 disk    
nvme0n1 259:1    0 931.5G  0 disk
```


```sh

```

There is also a `-J` or `–json` option. If used, the command outputs the information in JSON format. This provides a structured view that is particularly useful for scripting and automation.

```sh
❯ lsblk -f -J  
```
```json
{  
  "blockdevices": [  
     {  
        "name": "sda",  
        "fstype": null,  
        "fsver": null,  
        "label": null,  
        "uuid": null,  
        "fsavail": null,  
        "fsuse%": null,  
        "mountpoints": [  
            null  
        ],  
        "children": [  
           {  
              "name": "sda1",  
              "fstype": "vfat",  
              "fsver": "FAT32",  
              "label": "PORTABLE_WD",  
              "uuid": "C9B2-[....]",  
              "fsavail": null,  
              "fsuse%": null,  
              "mountpoints": [  
                  null  
              ]  
           }  
        ]  
     },{  
        "name": "zram0",  
        "fstype": null,  
        "fsver": null,  
        "label": null,  
        "uuid": null,  
        "fsavail": null,  
        "fsuse%": null,  
        "mountpoints": [  
            "[SWAP]"  
        ]  
     },{  
        "name": "nvme1n1",  
        "fstype": null,  
        "fsver": null,  
        "label": null,  
        "uuid": null,  
        "fsavail": null,  
        "fsuse%": null,  
        "mountpoints": [  
            null  
        ],  
        "children": [  
           {  
              "name": "nvme1n1p1",  
              "fstype": "vfat",  
              "fsver": "FAT32",  
              "label": null,  
              "uuid": "3C65-[....]",  
              "fsavail": "579.8M",  
              "fsuse%": "3%",  
              "mountpoints": [  
                  "/boot/efi"  
              ]  
           },{  
              "name": "nvme1n1p2",  
              "fstype": "ext4",  
              "fsver": "1.0",  
              "label": null,  
              "uuid": "73726fe4-[....]",  
              "fsavail": "445.6M",  
              "fsuse%": "47%",  
              "mountpoints": [  
                  "/boot"  
              ]  
           },{  
              "name": "nvme1n1p3",  
              "fstype": "btrfs",  
              "fsver": null,  
              "label": "fedora",  
              "uuid": "e5e3aab0-[....]",  
              "fsavail": "1.4T",  
              "fsuse%": "24%",  
              "mountpoints": [  
                  "/home", "/"  
              ]  
           }  
        ]  
     },{  
        "name": "nvme0n1",  
        "fstype": null,  
        "fsver": null,  
        "label": null,  
        "uuid": null,  
        "fsavail": null,  
        "fsuse%": null,  
        "mountpoints": [  
            null  
        ],  
        "children": [  
           {  
              "name": "nvme0n1p1",  
              "fstype": "btrfs",  
              "fsver": null,  
              "label": "fedora",  
              "uuid": "e5e3aab0-[....]",  
              "fsavail": null,  
              "fsuse%": null,  
              "mountpoints": [  
                  null  
              ]  
           }  
        ]  
     }  
  ]  
}

```