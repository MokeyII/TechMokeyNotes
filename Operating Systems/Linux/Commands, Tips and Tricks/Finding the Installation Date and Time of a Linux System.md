---
title: "Finding the Installation Date and Time of a Linux System"
date: 2024-12-13
tags:
  - Linux
  - System Administration
  - Troubleshooting
categories:
  - Guides
  - Linux
  - Tools
summary: "Learn how to find the date and time when a Linux operating system was installed using commands like `stat` and `rpm`."
author: "TheTechMokey"
notes:
  - "The `stat` command retrieves the file system's creation date, which often corresponds to the OS installation time."
  - "Using `rpm` provides the install date of the `basesystem` package, a core component of many Linux distributions."
warnings:
  - "The `stat` command's output depends on file system support for creation timestamps."
  - "Package installation dates retrieved by `rpm` may not reflect the exact OS installation time in some cases."
---


## Find Date and Time Linux OS Was Installed

> [!NOTE] Note
> The `stat` command retrieves the file system's creation date, which often corresponds to the OS installation time.
> The `stat` command's output depends on file system support for creation timestamps.

```bash
stat / | awk '/Birth: /{print $2 " " substr($3,1,5)}'
```
### Birth
```bash
stat /
```
```
...output omitted...
 Birth: 2024-09-06 02:36:14.505252651 -0400

```
### rpm basesystem

> [!NOTE] Note
> Using `rpm` provides the install date of the `basesystem` package, a core component of many Linux distributions
> Package installation dates retrieved by `rpm` may not reflect the exact OS installation time in some cases.

```bash
sudo rpm -qi basesystem | grep -i "install date"
```
```
...output omitted...
Install Date: Sun 14 Apr 2024 06:57:13 PM EDT
```