---
title: "Pacman: The Package Manager for Arch Linux and Its Derivatives"
date: 2024-12-13
tags:
  - Linux
  - Arch Linux
  - Package Manager
  - EndeavourOS
categories:
  - Guides
  - Package Management
summary: "A comprehensive guide to using Pacman, the powerful package manager for Arch Linux and its derivatives, including key commands for installation, updates, and maintenance."
author: "TheTechMokey"
notes:
  - "This guide explains the essential Pacman commands for managing software packages in Arch Linux and its derivatives like EndeavourOS."
  - "Includes commands for updating, installing, searching, removing, and cleaning packages."
warnings:
  - "Use caution when cleaning the package cache to avoid removing necessary files."
sources:
  - "https://archlinux.org/pacman/"
---


# Pacman
`pacman` is the package manager for Arch Linux and all of it's derivatives including EndeavourOS. It facilitates the installation, updating and removal of the software packages, ensuring that users have access to the latest software versions while managing dependencies automatically.

## Key `pacman` commands
### Update Package Database and System:
```bash
sudo pacman -Syu 
```
Synchronizes the package database and upgrades all out-of-date packages.
## Install a Package:
```bash
sudo pacman -S <package_name>
```
Installs the specified package from the repositories.
## Search for Packages:
```bash
pacman -Ss <keyword>
```
earches for installed packages matching the keyword.
Searches for packages in the repositories matching the keyword.
```bash
pacman -Qs <keyword>
```
Searches for installed packages matching the keyword.
## Remove a Package:
```bash
sudo pacman -R <package_name>
```
Removes the specified package but leaves its dependencies.
```bash
sudo pacman -Rs <package_name>
```
## Clean Package Cache:
```bash
sudo pacman -Sc
```
Removes uninstalled packages from the cache.
## List Installed Packages:
```bash
pacman -Q
```
Lists all installed packages.
```bash
pacman -Qe
```
