---
title: "Fixing Steam Flatpak Directory Issues"
date: 2024-12-13
tags:
  - Linux
  - Flatpak
  - Steam
  - Gaming
  - Troubleshooting
categories:
  - Guides
  - Linux
  - Gaming
  - Troubleshooting
summary: "A step-by-step guide to resolving directory issues caused by Steam installed via Flatpak, using a Python script to populate missing desktop entries."
author: "TheTechMokey"
notes:
  - "This guide explains how to use the steam-desktop-updater script to fix Steam Flatpak directory issues."
  - "Python and its necessary libraries must be installed to run the script."
sources:
  - "https://github.com/gasinvein/steam-desktop-updater"
  - "Steam Flatpak documentation"
warnings:
  - "Ensure you have Python and required libraries installed before running the script."
  - "Run the script carefully, as it modifies Steam's directory structure."
---


This is caused by Steam data being installed into it's own directory and not into the correct directory due to install steam via [[Flatpak - A Universal Packaging System for Linux]]

Install Python package manager
```bash
sudo dnf install python3-pip
```
Install Pre-Reqs for the python script
```bash
python3 -m pip install --user pillow vdf steam
```

Change Directory to Downloads
```bash
cd ~/Downloads
```

Clone github repo
```bash
sudo git clone https://github.com/gasinvein/steam-desktop-updater.git
```

Change directory or run from directory
```bash
cd steam-desktop-updater
```

Run the script for Steam Flatpak
```bash
./steam_desktop_updater.py ~/.var/app/com.valvesoftware.Steam/data/Steam
```

Wait for apps to populate

Sources
https://github.com/gasinvein/steam-desktop-updater