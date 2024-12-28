---
title: "How to Create a Bootable USB Drive with Balena Etcher"
date: 2024-12-13
tags:
  - Balena Etcher
  - USB Drive
  - Bootable Media
  - ISO
  - Linux
  - Windows
  - macOS
categories:
  - Software Guides
  - Operating Systems
  - Tools
author: "TheTechMokey"
summary: "Learn how to create a bootable USB drive using Balena Etcher, a user-friendly tool for flashing OS images to SD cards and USB drives."
features:
  - Cross-platform support for Windows, macOS, and Linux.
  - Step-by-step guide to flashing OS images.
  - Tips for safely creating bootable drives.
related_links:
  - "Balena Etcher Official Website: https://etcher.balena.io/"
  - "ISO Files: Trusted Sources and Usage: https://www.linux.org/"
  - "Guide to Bootable Media Creation: https://www.howtogeek.com/"
---


![[Pasted image 20241014024559.png]]
# How to Create a Bootable USB Drive with Balena Etcher

## Introduction
Balena Etcher is a free and open-source tool that allows you to flash OS images to SD cards and USB drives easily and safely. It's user-friendly and works on Windows, macOS, and Linux.

## Downloading Balena Etcher

### For Windows:
1. Visit the [Balena Etcher download page](https://etcher.balena.io/#download-etcher).
2. Download the Etcher installer for Windows.
3. Run the installer and follow the on-screen instructions to install Etcher.

### For macOS:
1. Visit the [Balena Etcher download page](https://etcher.balena.io/#download-etcher).
2. Download the Etcher installer for macOS.
3. Run the installer and follow the on-screen instructions to install Etcher.

### For Linux:
1. Visit the [Balena Etcher download page](https://etcher.balena.io/#download-etcher).
2. Download the Etcher installer for Linux.
3. Extract the downloaded file.
4. Open a terminal and navigate to the extracted folder.
5. Run the following command to install Etcher:
Debian/Ubuntu
```bash
sudo apt install ./balena-etcher_*.deb
```
## Using Balena Etcher

### Step 1: Download the OS Image

Download the ISO file of the operating system you want to install. Make sure it's from a trusted source.

### Step 2: Open Balena Etcher

Launch Balena Etcher on your computer.

### Step 3: Select the Image

Click on the "Select image" button and browse to the location of the downloaded ISO file.

### Step 4: Select the Target Drive

Click on the "Select target" button and choose the USB drive you want to use. Be careful to select the correct drive, as all data on the drive will be erased.

### Step 5: Flash the Image

Click the "Flash!" button to start the process. Etcher will verify the data after flashing to ensure everything was written correctly.

### Step 6: Complete the Process

Wait for the flashing process to complete. Etcher will notify you once it's done.