---
title: "Installing Lutris on Linux via Flatpak"
date: 2024-12-14
tags:
  - Gaming
  - Linux
  - Lutris
  - Flatpak
  - Game Launchers
categories:
  - Gaming
  - Linux Applications
author: "TheTechMokey"
summary: "A step-by-step guide to installing Lutris on Linux using Flatpak, providing a unified interface for managing games from various sources."
features:
  - Manage native Linux, Windows, emulated, and web-based games.
  - Simplified installation and configuration of games on Linux.
  - Consistent installation experience using Flatpak.
related_links:
  - "Official Lutris Website: https://lutris.net/"
  - "Flathub Repository: https://flathub.org/"
  - "Flatpak Documentation: https://docs.flatpak.org/"
---



Lutris is a versatile [[Understanding Game Launchers]] designed to streamline the process of managing and playing games on [[Linux]]. It supports a wide range of game sources, including native Linux games, Windows games (via Wine), emulators, and even web-based games. By providing a unified interface, Lutris simplifies the installation, configuration, and launching of games, making it an essential tool for Linux gamers.

### Installing Lutris with Flatpak on Linux

Flatpak is a universal packaging system for Linux that allows you to install applications in a consistent environment across different distributions. Installing Lutris via Flatpak ensures that you get the latest version of the software with all necessary dependencies bundled together.

Here’s a step-by-step guide to installing Lutris using Flatpak:

1. **Install Flatpak**:  
    First, ensure that Flatpak is installed on your system. You can usually install it from your distribution’s package manager. For example, on Debian-based systems like Ubuntu, you can use:
    
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
    
3. **Install Lutris**:  
    Once Flatpak and the Flathub repository are set up, you can install Lutris with the following command:
    
    ```bash
    flatpak install flathub net.lutris.Lutris
    ```
    
4. **Run Lutris**:  
    After the installation is complete, you can launch Lutris using the following command:
    
    ```bash
    flatpak run net.lutris.Lutris
    ```
    

By following these steps, you will have Lutris installed on your Linux system via Flatpak, ready to manage and launch your games efficiently.