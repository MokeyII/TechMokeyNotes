---
title: "Proxmox Server Setup Guide"
date: 2024-12-13
tags:
  - Proxmox
  - Virtualization
  - Server Setup
  - Linux
  - Open Source
categories:
  - Virtualization
  - Server Management
author: "TheTechMokey"
summary: "A comprehensive guide to setting up a Proxmox server for virtual machines and containers, including requirements, installation, and updates."
features:
  - Supports KVM for virtual machines and LXC for containers.
  - Includes network and storage configuration for optimal performance.
  - Offers a web interface for easy management.
related_links:
  - "Proxmox VE Official Website: https://www.proxmox.com/"
  - "Proxmox VE ISO Downloads: https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso"
  - "Proxmox Documentation: https://pve.proxmox.com/pve-docs/"
  - "[Beelink AMD Ryzen 7 5800H Mini PC](https://www.amazon.com/dp/B0CRKXMKDT?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1)"
---


# Proxmox Server Setup Guide

![[Pasted image 20241014194204.png|150]]
## Introduction
Proxmox is an open-source server virtualization platform where you can create virtual machines, containers, storage, and networks. It uses Kernel-based Virtual Machine (KVM) and Linux Containers (LXC). This guide will walk you through the process of setting up a Proxmox server from scratch, including updates and basic configuration.

## Requirements
Check out the [Proxmox VE requirements](https://www.proxmox.com/en/proxmox-virtual-environment/requirements):
- Intel 64 or AMD64 with Intel VT/AMD-V CPU flag.
- Memory: Minimum 2 GB for OS and Proxmox VE services. Additional memory is required for guests and approximately 1 GB of memory for every TB of used storage for Ceph or ZFS.
- Fast and redundant storage, best results with SSD disks.
- OS storage: Hardware RAID with batteries protected write cache (BBU) or non-RAID with ZFS and SSD cache.
- VM storage: Local storage using hardware RAID with battery backed write cache (BBU) or non-RAID for ZFS. Neither ZFS nor Ceph are compatible with a hardware RAID controller. Shared and distributed storage are also possible.
- Redundant Gbit NICs, additional NICs depending on the preferred storage technology and cluster setup. 10 Gbit and higher is also supported.
- For PCI(e) passthrough, a CPU with VT-d/AMD-d CPU flag is needed.

### What does Mokey use?
- [2x Beelink AMD Ryzen 7 5800H Mini PC](https://www.amazon.com/dp/B0CRKXMKDT?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1) Up to 4.4Ghz, 32GB DDR4 1TB NVME 2280 SSD Mini Computers, WiFi6/BT5.2, 4K Triple Display Mini Desktop Computer

## Step 1: Download Proxmox VE ISO
Visit the Proxmox website and download the latest [Proxmox VE ISO image](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso).

## Step 2: Create a Bootable USB Drive
Boot from USB or CD/DVD. This example will use USB. Use a tool like [[How to Create a Bootable USB Drive with Balena Etcher|Balena Etcher]] or [[How to Download and Use Ventoy|Ventoy]] to write the Proxmox VE ISO to the USB drive.

## Step 3: Boot from USB
Insert the USB drive into your server and boot from it.

## Step 4: Start Proxmox Installation
Follow the on-screen instructions to start the installation process.

## Step 5: Choose Installation Target
Select the target hard drive for the installation.

## Step 6: Set Password
Set a root password for the server.

## Step 7: Configure Network
Set a static IP address for the Proxmox server.

## Step 8: Web Interface Configuration
After the installation completes, access the web interface by browsing to the server's IP address.

## Step 9: Upload ISO Images
Upload the ISO images of the operating systems you want to use.

## Step 10: Create Virtual Machines
Create virtual machines using the uploaded ISO images.

## Step 11: Update Proxmox
Run the following commands to update Proxmox:
```bash
apt update
apt upgrade
```
