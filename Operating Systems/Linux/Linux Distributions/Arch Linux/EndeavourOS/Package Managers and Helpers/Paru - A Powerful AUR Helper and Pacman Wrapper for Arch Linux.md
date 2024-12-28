---
title: "Paru: A Powerful AUR Helper and Pacman Wrapper for Arch Linux"
date: 2024-12-13
tags:
  - Linux
  - Arch Linux
  - EndeavourOS
  - AUR
  - Package Manager
categories:
  - Guides
  - Package Management
summary: "An in-depth guide to Paru, the modern AUR helper and Pacman wrapper for Arch Linux, highlighting its features, key commands, and differences from Yay."
author: "TheTechMokey"
notes:
  - "Paru is an advanced AUR helper written in Rust, designed to streamline package management for Arch Linux users."
  - "This guide includes a comparison with Yay and essential commands for searching, installing, and managing packages."
warnings:
  - "Always review PKGBUILD files before building packages from the AUR to ensure their safety."
sources:
  - "https://github.com/Morganamilo/paru"
  - "Arch Wiki: AUR Helpers"
---


# Paru
paru is an AUR (Arch User Repository) helper and pacman wrapper designed for Arch Linux and its derivatives, including EndeavourOS. It facilitates the process of searching for, installing, and managing packages from both the official repositories and the AUR, streamlining package management tasks for users. 
## Differences between PARU and YAY

### Key Differences Between yay and paru

| **Aspect**               | **yay**                                                       | **paru**                                                                                               |
| ------------------------ | ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Language**             | Written in Go for simplicity and speed.                       | Written in Rust, leveraging Rust’s safety and performance features.                                    |
| **User Interface**       | Provides a straightforward and minimal user experience.       | More feature-rich and polished with a focus on user interaction.                                       |
| **Dependency Search**    | Shows fewer details during interactive dependency resolution. | Displays more details (e.g., version and repository) for dependencies during interactive installation. |
| **Configuration**        | Simple and minimal configuration.                             | Offers more configuration options, including colorized outputs and fine-tuning behaviors.              |
| **Focus on AUR Details** | Basic AUR metadata display.                                   | Provides more detailed information about AUR packages, including the maintainer and build times.       |
| **Security Features**    | Relies on standard AUR security practices.                    | Introduced a PKGBUILD diffing feature that highlights changes in PKGBUILD files before building.       |
| **Popularity**           | One of the older and more widely used AUR helpers.            | Newer but gaining traction rapidly due to its modern features.                                         |
| **Parallel Downloads**   | Supports parallel downloads (optional).                       | Supports parallel downloads by default for faster installations.                                       |
| **Customization**        | Limited built-in customization.                               | More customizable, including options for output color and formatting.                                  |
| **Speed and Efficiency** | Fast, but sometimes slower than `paru` for dependency checks. | Slightly faster in some cases, especially with AUR dependency handling.                                |

## Key `paru` Commands

### Search and Install Packages:
```bash
paru <package_name_or_search_term>
```
Interactively searches for and installs packages matching the provided name or term.
### Update System Packages:
```bash
paru
``` 
Synchronizes the package databases and updates all installed packages from both official repositories and the AUR.
### Upgrade AUR Packages Only:
```bash
paru -Sua
```
Checks for updates specifically in the AUR and upgrades the AUR packages to their latest versions.
### Display Package Information:
```bash
paru -Si <package_name>
```
Retrieves and displays detailed information about a specific package from the repositories or the AUR.
### Download PKGBUILD and Source Files:
```bash
paru --getpkgbuild <package_name>
```
Downloads the PKGBUILD file and other source files of a package from the AUR, allowing for manual inspection or modification.
### Display PKGBUILD Contents:**
```bash
paru --getpkgbuild --print <package_name>
```
Displays the contents of the PKGBUILD file for a package without downloading it, useful for reviewing build scripts.