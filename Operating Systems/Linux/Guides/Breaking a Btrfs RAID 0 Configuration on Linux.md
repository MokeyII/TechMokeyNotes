---
title: "Breaking a Btrfs RAID 0 Configuration on Linux"
date: 2024-12-13
tags:
  - Linux
  - Btrfs
  - RAID
  - File Systems
categories:
  - Guides
  - System Administration
  - Advanced Linux
summary: "Step-by-step guide to safely break a Btrfs RAID 0 configuration between two NVMe drives, with detailed commands and recommendations."
author: TheTechMokey
warning: "This operation involves advanced file system modifications. Ensure data backup and use a live USB for safety."
---


# Important Notes

> [!NOTE]
> This example shows how to break a Btrfs RAID 0 configuration between 2 NVMEs.
> 
> ==**DO NOT**== do this if you are not comfortable with operating Linux
> 
> If you continue, ensure all data is backed up and you have a boot disc ready to go.
> 
> **Recommendation:** Use a live USB when doing this. 

# Understand your setup
Check your Btrfs RAID layout
```sh
sudo btrfs filesystem show
```
Output:
```sh
sudo btrfs filesystem show      
Label: 'fedora'  uuid: somerand-doms-trin-g-ofnumbers12354  
       Total devices 2 FS bytes used 42.42GiB  
       devid    1 size 929.93GiB used 25.01GiB path /dev/nvme0n1p3  
       devid    2 size 929.93GiB used 25.01GiB path /dev/nvme1n1p1
```

Check Raid type and devices in the array
```sh
sudo btrfs filesystem df /
```
Output:
```sh
sudo btrfs filesystem df /  
Data, RAID0: total=46.00GiB, used=41.28GiB  
System, RAID1: total=8.00MiB, used=16.00KiB  
Metadata, RAID1: total=2.00GiB, used=1.14GiB  
GlobalReserve, single: total=106.09MiB, used=0.00B
```
# Back up all data!
Make sure you backup all data! 
If the RAID array contains your root file system (`/`), consider using a live USB for this process.

# Breaking the raid
Explicitly allow the operation on system chunks, use the `--force` flag:
```sh
sudo btrfs balance start -mconvert=single -sconvert=single --force /
```
Output:
```sh
sudo btrfs balance start -mconvert=single -sconvert=single --force /
Done, had to relocate 3 out of 26 chunks
```
# Convert Data Chunks to Single
After converting metadata and system chunks, convert the data chunks to a single disk.
```sh
sudo btrfs balance start -dconvert=single /  
```
Output:
```sh
sudo btrfs balance start -dconvert=single /  
Done, had to relocate 23 out of 26 chunks
```
# Validate the conversion
Once the commands complete, check the RAID levels to ensure they are all set to `single`
```
sudo btrfs filesystem df /  
```
Output:
```sh
sudo btrfs filesystem df /  
Data, single: total=43.00GiB, used=41.28GiB  
System, single: total=32.00MiB, used=16.00KiB  
Metadata, single: total=2.00GiB, used=1.15GiB  
GlobalReserve, single: total=110.91MiB, used=0.00B
```

# Remove the device from Btrfs
Now that the file system no longer relies on RAID, remove the device from the Btrfs array.
```sh
sudo btrfs device remove /dev/nvme1n1p1 /
```

# Balance the File system
After successfully removing the device, re-balance the file system to ensure data is properly distributed.
```sh
sudo btrfs balance start /
```
Output:
```sh
sudo btrfs balance start /
WARNING:  
  
       Full balance without filters requested. This operation is very  
       intense and takes potentially very long. It is recommended to  
       use the balance filters to narrow down the scope of balance.  
       Use 'btrfs balance start --full-balance' option to skip this  
       warning. The operation will start in 10 seconds.  
       Use Ctrl-C to stop it.  
10 9 8 7 6 5 4 3 2 1  
Starting balance without any filters.  
Done, had to relocate 46 out of 46 chunks
```

# Validate Changes
Finally, confirm that `/dev/nvme1n1p1` has been removed.
```sh
sudo btrfs filesystem show  
```
Output:
```sh
sudo btrfs filesystem show  
Label: 'fedora'  uuid: somerand-doms-trin-g-ofnumbers12354  
       Total devices 1 FS bytes used 42.42GiB  
       devid    1 size 929.93GiB used 45.03GiB path /dev/nvme0n1p3
```

# Reboot the system
Cross your fingers :LiSmile:
```sh
systemctl reboot
```

# Welcome Back!
Now you have an NVME you can use for whatever you want agan!