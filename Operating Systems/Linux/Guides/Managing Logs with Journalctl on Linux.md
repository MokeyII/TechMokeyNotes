---
title: "Managing Logs with Journalctl on Linux"
date: 2024-12-13
tags:
  - Linux
  - System Administration
  - Logs
  - Journalctl
categories:
  - Guides
  - Troubleshooting
  - Logging
summary: "Comprehensive guide to using Journalctl for managing and troubleshooting logs on Linux, including configuration, log size management, and advanced filtering techniques."
author: "TheTechMokey"
notes:
  - "Ensure changes to journald.conf are made in the `/etc/systemd/` directory for persistence."
  - "Regularly monitor log sizes to prevent excessive disk usage."
---

# Journalctl
## Finding your Journald.conf
```bash
sudo find / -type f -name journald.conf
```
```
...output omitted...
/usr/lib/systemd/journald.conf
```
### Copy the config
```bash
sudo cp /usr/lib/systemd/journald.conf /etc/systemd/
```
### Configure journald.conf
```bash
sudo nano /etc/systemd/journald.conf
```

```
SystemMaxUse=512M
SystemKeepFree=1G
MaxRetentionSec=1month
MaxFileSec=1week
```
#### Restart systemd-journald
```bash
sudo systemctl restart systemd-journald
```
## List Boots
```bash
journalctl --list-boots
```
## Log size
Validate disk usage
```bash
journalctl --disk-usage
```
## Verify Log consistency
```bash
journalctl --verify
```
## Reducing Logs (Vacuum)
```
 --vacuum-size=BYTES   Reduce disk usage below specified size
 --vacuum-files=INT    Leave only the specified number of journal files
 --vacuum-time=TIME    Remove journal files older than specified time
```
### Journal Size
```bash
sudo journalctl --vacuum-size=200M
```
### Journal File Limit
```bash
sudo journalctl --vacuum-files-20
	```
# Searching Journalctl
## Show logging
```bash
journalctl
```
## Reverse Logging
```bash
journalctl -r
```
## Tail Logs in realtime
```bash
journalctl -f
```
You can add `-f` to the end of most `journalctl` commands
## Find keywords using grep
```bash
journalctl | grep "keyword"
```
## Filter Logs by priority
```bash
journalctl -u <service_name>
```
## Filter Logs by time range
```bash
journalctl --since "2024-09-01" --until "2024-09-30"
```
