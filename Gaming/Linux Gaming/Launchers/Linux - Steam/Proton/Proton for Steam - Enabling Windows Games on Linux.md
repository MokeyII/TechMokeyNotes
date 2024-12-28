---
title: "Proton for Steam: Enabling Windows Games on Linux"
date: 2024-12-14
tags:
  - Gaming
  - Linux
  - Steam
  - Proton
  - Compatibility Tools
categories:
  - Gaming
  - Linux Applications
author: "TheTechMokey"
summary: "Proton is a compatibility layer developed by Valve to enable Windows games to run seamlessly on Linux through the Steam client."
features:
  - Seamless Steam integration for running Windows games on Linux.
  - DirectX to Vulkan translation with DXVK and VKD3D for enhanced compatibility.
  - Performance optimizations tailored for gaming on Linux.
  - Regular updates to improve compatibility with new titles.
  - Simple configuration options via the Steam client.
related_links:
  - "Valve Proton GitHub: https://github.com/ValveSoftware/Proton"
  - "DXVK GitHub: https://github.com/doitsujin/dxvk"
  - "VKD3D GitHub: https://github.com/HansKristian-Work/vkd3d-proton"
  - "Steam Play Compatibility: https://store.steampowered.com/steamplay/"
---


### What is Proton for Steam?

Proton is a compatibility layer developed by Valve Corporation, designed to enable Windows games to run on Linux-based operating systems through the Steam client. It is built on top of Wine (Wine Is Not an Emulator), an open-source compatibility layer that allows Windows applications to run on Unix-like operating systems. Proton integrates additional tools and libraries, such as DXVK (DirectX to Vulkan translation) and VKD3D (Direct3D 12 to Vulkan translation), to improve performance and compatibility for gaming.

### Key Features of Proton

1. **Seamless Integration with Steam**:
   - Proton is integrated directly into the Steam client, allowing users to install and run Windows games on Linux as if they were native Linux games.
   - Users can enable Proton for all games or on a per-game basis through the Steam Play settings.

2. **DirectX to Vulkan Translation**:
   - Proton uses DXVK to translate DirectX 9, 10, and 11 calls to Vulkan, a modern graphics API that is well-supported on Linux.
   - VKD3D is used for translating Direct3D 12 calls to Vulkan, enabling newer games that use Direct3D 12 to run on Linux.

3. **Improved Performance**:
   - Proton includes performance optimizations and patches that are not present in the standard Wine distribution, resulting in better performance for many games.
   - It also supports multi-threaded performance improvements and other enhancements specific to gaming.

4. **Compatibility Enhancements**:
   - Proton includes various libraries and tools to improve compatibility with Windows games, such as FAudio for better audio support and esync/fsync for improved threading performance.
   - Regular updates and community contributions help expand the list of compatible games.

5. **Easy Configuration**:
   - Proton can be configured through the Steam client, making it accessible even to users who are not familiar with Wine or Linux gaming.
   - Advanced users can customize Proton settings and use environment variables to tweak performance and compatibility.

### How to Enable and Use Proton on [[Steam]]

1. **Install Steam**:
   - Ensure that the Steam client is installed on your Linux system. You can usually install it from your distribution's package manager.

   **For Debian-based systems**:
   ```bash
   sudo apt install steam
   ```

   **For [[Fedora]]**:
   ```bash
   sudo dnf install steam
   ```

   **For OSTree-based systems (e.g., Fedora Silverblue)**:
   ```bash
   sudo rpm-ostree install steam
   ```

   **For [[Flatpak - A Universal Packaging System for Linux]]**:
   - First, ensure Flatpak is installed and Flathub is added as a repository:
     ```bash
     sudo apt install flatpak
```

	For [[Fedora]] Based Systems
    ```bash
    sudo dnf install flatpak 
     flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
     ```
   - Then, install [[Steam]] via [[Flatpak]]:
     ```bash
     flatpak install flathub com.valvesoftware.Steam
     ```

2. **Enable Steam Play**:
   - Open the Steam client and go to `Steam` > `Settings` > `Compatibility` > `Enable Steam Play`.
   - Check the box for "Enable Steam Play for supported titles" to use Proton for games that Valve has officially tested and approved.
   - Optionally, check the box for "Enable Steam Play for all other titles" to use Proton for any Windows game in your library.

3. **Select Proton Version**:
   - In the same Steam Play settings menu, you can choose the version of Proton you want to use. Valve regularly releases new versions with improvements and bug fixes.
   - It's often a good idea to use the latest stable version, but you can also experiment with different versions if you encounter issues.

4. **Install and Play Games**:
   - Browse your Steam library and install any Windows game as you normally would.
   - Steam will automatically use Proton to run the game on your Linux system.
   - You can also right-click on a game, go to `Properties` > `Compatibility`, and select a specific version of Proton to use for that game.

### Key Features of Proton

1. **Seamless Integration with Steam**:
    
    - Proton is integrated directly into the Steam client, allowing users to install and run Windows games on Linux as if they were native Linux games.
    - Users can enable Proton for all games or on a per-game basis through the Steam Play settings.
2. **DirectX to Vulkan Translation**:
    
    - Proton uses DXVK to translate DirectX 9, 10, and 11 calls to Vulkan, a modern graphics API that is well-supported on Linux.
    - VKD3D is used for translating Direct3D 12 calls to Vulkan, enabling newer games that use Direct3D 12 to run on Linux.
3. **Improved Performance**:
    
    - Proton includes performance optimizations and patches that are not present in the standard Wine distribution, resulting in better performance for many games.
    - It also supports multi-threaded performance improvements and other enhancements specific to gaming.
4. **Compatibility Enhancements**:
    
    - Proton includes various libraries and tools to improve compatibility with Windows games, such as FAudio for better audio support and esync/fsync for improved threading performance.
    - Regular updates and community contributions help expand the list of compatible games.
5. **Easy Configuration**:
    
    - Proton can be configured through the Steam client, making it accessible even to users who are not familiar with Wine or Linux gaming.
    - Advanced users can customize Proton settings and use environment variables to tweak performance and compatibility.