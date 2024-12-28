---
title: "Installing World of Warcraft on Windows and Linux"
date: 2024-12-14
tags:
  - Gaming
  - Linux
  - Windows
  - World of Warcraft
  - Wine
categories:
  - Gaming
  - Linux Gaming
author: "TheTechMokey"
summary: "A comprehensive guide to installing World of Warcraft on Windows and Linux using various methods like Wine, Lutris, and Heroic Games Launcher."
features:
  - Step-by-step instructions for installing WoW on multiple platforms.
  - Methods include Wine, Lutris, and Heroic Games Launcher for Linux users.
  - Tips for configuring and optimizing the game on Linux.
related_links:
  - "Battle.net Official Site: https://www.blizzard.com/en-us/apps/battle.net/desktop"
  - "Heroic Games Launcher: https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher"
  - "Lutris Gaming Platform: https://lutris.net/"
  - "Wine Compatibility Layer: https://www.winehq.org/"
---


World of Warcraft (WoW) is a massively multiplayer online role-playing game (MMORPG) developed and published by Blizzard Entertainment. Released in 2004, it has become one of the most popular and influential MMORPGs in the world. Set in the high-fantasy universe of Azeroth, players create characters, complete quests, explore vast landscapes, engage in player-versus-environment (PvE) and player-versus-player (PvP) combat, and participate in large-scale raids and dungeons.

### Installing World of Warcraft

#### On Windows

1. **Download the Battle.net App**:
    
    - Visit the official [Battle.net website](https://www.blizzard.com/en-us/apps/battle.net/desktop) and download the Battle.net desktop app.
2. **Install the Battle.net App**:
    
    - Run the downloaded installer and follow the on-screen instructions to install the Battle.net app.
3. **Log in to Battle.net**:
    
    - Open the Battle.net app and log in with your Blizzard account. If you don't have an account, you can create one.
4. **Install World of Warcraft**:
    
    - In the Battle.net app, find World of Warcraft in the list of games and click on it.
    - Click the "Install" button and follow the prompts to install the game.

#### On Debian-based Systems (e.g., Ubuntu)

1. **Install Wine**:
    
    - Wine is a compatibility layer that allows Windows applications to run on Linux. Install Wine using the following commands:
        
        ```bash
        sudo dpkg --add-architecture i386
        sudo apt update
        sudo apt install wine64 wine32
        ```
        
2. **Download the Battle.net Installer**:
    
    - Visit the official [Battle.net website](https://www.blizzard.com/en-us/apps/battle.net/desktop) and download the Battle.net installer.
3. **Run the Battle.net Installer with Wine**:
    
    - Navigate to the directory where you downloaded the installer and run it with Wine:
        
        ```bash
        wine Battle.net-Setup.exe
        ```
        
4. **Install World of Warcraft**:
    
    - Follow the same steps as on Windows to log in to the Battle.net app and install World of Warcraft.

#### On [[Fedora]]

1. **Install Wine**:
    
    - Install Wine using the following commands:
        
        ```bash
        sudo dnf install wine
        ```
        
2. **Download the Battle.net Installer**:
    
    - Visit the official [Battle.net website](https://www.blizzard.com/en-us/apps/battle.net/desktop) and download the Battle.net installer.
3. **Run the Battle.net Installer with Wine**:
    
    - Navigate to the directory where you downloaded the installer and run it with Wine:
        
        ```bash
        wine Battle.net-Setup.exe
        ```
        
4. **Install World of Warcraft**:
    
    - Follow the same steps as on Windows to log in to the Battle.net app and install World of Warcraft.

#### Using [[Heroic Games Launcher -  Seamless Epic Games on Linux]]

Heroic Games Launcher is primarily used for Epic Games Store games, but you can add custom games and launchers.

1. **Install Heroic Games Launcher**:
    
    - Follow the instructions on the [Heroic Games Launcher GitHub page](https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher) to install the launcher.
2. **Add Battle.net as a Custom Game**:
    
    - Open Heroic Games Launcher and go to the "Library" tab.
    - Click on "Add Game" and select "Add a Non-Epic Game."
    - Browse to the Battle.net installer and add it.
3. **Run the Battle.net Installer**:
    
    - Launch the Battle.net installer from Heroic Games Launcher and follow the installation steps.
4. **Install World of Warcraft**:
    
    - Follow the same steps as on Windows to log in to the Battle.net app and install World of Warcraft.

#### Using [[Installing Lutris on Linux via Flatpak]]

Lutris is a gaming platform for Linux that helps manage and run games from various sources, including Windows games via Wine.

1. **Install Lutris**:
    
    - Install Lutris using your distribution's package manager.
    
    **For Debian-based systems**:
    
    ```bash
    sudo add-apt-repository ppa:lutris-team/lutris
    sudo apt update
    sudo apt install lutris
    ```
    
    **For Fedora**:
    
    ```bash
    sudo dnf install lutris
    ```
    
2. **Install Wine Dependencies**:
    
    - Ensure you have the necessary Wine dependencies installed. Lutris usually handles this, but you can manually install them if needed.
3. **Add World of Warcraft to Lutris**:
    
    - Open Lutris and click on the "Search the Lutris website for installers" button.
    - Search 3. - for "World of Warcraft" and select the appropriate installer script from the Lutris website.
    - Click "Install" and follow the prompts to download and install the game. Lutris will handle the configuration of Wine and any necessary dependencies.
4. **Run World of Warcraft**:
    
    - Once the installation is complete, you can launch World of Warcraft directly from the Lutris interface.

### Summary

World of Warcraft is a popular MMORPG that can be installed and played on various operating systems, including Windows and Linux. Here’s a quick summary of the installation methods:

- **Windows**: Use the Battle.net app to download and install World of Warcraft.
- **Debian-based Systems**: Install Wine, download the Battle.net installer, and run it with Wine.
- **Fedora**: Install Wine, download the Battle.net installer, and run it with Wine.
- **Heroic Games Launcher**: Add Battle.net as a custom game and install World of Warcraft through the Battle.net app.
- **Lutris**: Use Lutris to manage the installation and configuration of World of Warcraft, leveraging Wine for compatibility.

By following these steps, you can enjoy World of Warcraft on your preferred operating system.