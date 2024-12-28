---
title: "How to Download and Use Ventoy"
date: 2024-12-13
tags:
  - Ventoy
  - Bootable USB
  - ISO Files
  - Linux
  - Windows
  - Multi-OS
categories:
  - Software Tools
  - Operating Systems
  - Bootable Media
author: "TheTechMokey"
summary: "A step-by-step guide to downloading and using Ventoy, a tool for creating multi-boot USB drives with support for ISO, WIM, IMG, and other formats."
features:
  - Supports multiple bootable images on one USB drive.
  - Easy-to-use interface for both Windows and Linux.
  - No need for ISO extraction; boot directly from files.
related_links:
  - "Ventoy Official Website: https://www.ventoy.net/"
  - "Multi-Boot USB Tips: https://www.howtogeek.com/"
  - "Supported Image Formats by Ventoy: https://www.ventoy.net/en/doc_supported.html"
---


![[Pasted image 20241014024318.png]]
# How to Download and Use Ventoy

## Introduction
Ventoy is a free and open-source tool that allows you to create bootable USB drives for installing operating systems. It supports various types of storage devices like USBs, local disks, SSDs, NVMe, and SD cards. With Ventoy, you can directly boot from ISO/WIM/IMG/VHD(x)/EFI files without the need for extraction.

## Downloading Ventoy

### For Windows:
1. Visit the [Ventoy download page](https://www.ventoy.net/en/download.html).
2. Download the Ventoy installation package for Windows (e.g., `ventoy-x.x.xx-windows.zip`).
3. Extract the downloaded zip file.
4. Open the extracted folder and run `Ventoy2Disk.exe`.
5. Select the USB drive you want to install Ventoy on and click the "Install" button.
6.  After installation, copy the ISO files of the operating systems you want to install to the USB drive.
7. Reboot your computer and select the USB drive as the boot device.
8. Ventoy will present a menu where you can choose which ISO to boot from.

### For Linux:
1. Visit the [Ventoy download page](https://www.ventoy.net/en/download.html).
2. Download the Ventoy installation package for Linux (e.g., `ventoy-x.x.xx-linux.tar.gz`).
3. Extract the downloaded tar.gz file.
4. Open a terminal and navigate to the extracted folder.
5. Run the following command, replacing `/dev/sdX` with the device name of your USB drive:
```bash
sudo ./Ventoy2Disk.sh -i /dev/sdX
```
6. After installation, copy the ISO files of the operating systems you want to boot from to the root of the USB drive.
7. Reboot your computer and select the USB drive as the boot device.
8. Ventoy will present a menu where you can choose which ISO to boot from.