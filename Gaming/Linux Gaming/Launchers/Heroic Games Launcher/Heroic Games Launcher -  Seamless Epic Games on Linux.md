---
title: "Heroic Games Launcher: Seamless Epic Games on Linux"
date: 2024-12-14
tags:
  - Gaming
  - Linux
  - Game Launchers
  - Epic Games Store
categories:
  - Gaming
  - Linux Applications
author: "TheTechMokey"
summary: "Heroic Games Launcher provides Linux users with a user-friendly interface for managing and playing Epic Games Store titles, leveraging Legendary for seamless game management."
features:
  - Install and play Epic Games Store titles on Linux with ease.
  - Supports multiple installation methods including Flatpak, AppImage, and native packages.
  - Versatile game launcher with support for other game sources.
related_links:
  - "Heroic Games Launcher GitHub: https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher"
  - "Flatpak Installation Guide: https://flatpak.org/setup/"
  - "Flathub Heroic Games Launcher Page: https://flathub.org/apps/details/com.heroicgameslauncher.hgl"
  - "Legendary CLI Tool: https://github.com/derrod/legendary"
---



Heroic Games Launcher is an open-source [[Understanding Game Launchers]] designed to provide a user-friendly interface for managing and playing games from the Epic Games Store on [[Linux]]. It leverages the capabilities of the Legendary CLI tool to interact with the Epic Games Store, allowing users to download, install, and play their Epic games seamlessly on Linux. Heroic Games Launcher also supports other game sources, making it a versatile tool for Linux gamers.

### Installing Heroic Games Launcher on Linux

Heroic Games Launcher can be installed on Linux using various methods, including AppImage, Flatpak, and native package managers. Below are the steps to install Heroic Games Launcher using Flatpak, which ensures a consistent installation experience across different Linux distributions.

#### Method 1: Installing via Flatpak

1. **Install Flatpak**:  
    Ensure that Flatpak is installed on your system. You can usually install it from your distribution’s package manager. For example, on Debian-based systems like Ubuntu, you can use:
    
    ```bash
    sudo apt install flatpak
    ```
    
    On Fedora, you can use:
    
    ```bash
    sudo dnf install flatpak
    ```
    
2. **Add the Flathub Repository**:  
    Flathub is the primary source for Flatpak applications. Add the Flathub repository to your system with the following command:
    
    ```bash
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
    ```
    
3. **Install Heroic Games Launcher**:  
    Once Flatpak and the Flathub repository are set up, you can install Heroic Games Launcher with the following command:
    
    ```bash
    flatpak install flathub com.heroicgameslauncher.hgl
    ```
    
4. **Run Heroic Games Launcher**:  
    After the installation is complete, you can launch Heroic Games Launcher using the following command:
    
    ```bash
    flatpak run com.heroicgameslauncher.hgl
    ```