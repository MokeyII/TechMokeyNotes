---
title: "Installing and Running Steam on Linux"
date: 2024-12-14
tags:
  - Gaming
  - Linux
  - Steam
  - Flatpak
  - Fedora
  - Ubuntu
categories:
  - Gaming
  - Linux Applications
author: "TheTechMokey"
summary: "Learn how to install and run Steam on Linux, including Debian-based systems, Fedora, and Flatpak installations."
features:
  - Native Steam client support for Linux.
  - Step-by-step installation for Debian-based, Fedora, and Flatpak setups.
  - Access to native Linux and Windows games via Proton compatibility.
related_links:
  - "Official Steam for Linux: https://store.steampowered.com/linux"
  - "RPM Fusion Repository: https://rpmfusion.org/"
  - "Flathub: https://flathub.org/"
  - "Proton GitHub: https://github.com/ValveSoftware/Proton"
---


### Is Steam Available on [[Linux]]?

Yes, Steam is available on Linux. Valve Corporation, the developer of Steam, has provided a native Linux client that allows users to access and play a wide range of games on their Linux systems. Steam on Linux supports a variety of games, including native Linux games and Windows games through compatibility layers like Proton.

### How to Install and Run Steam on Linux

The installation process for Steam varies slightly depending on your Linux distribution. Below are the steps for installing Steam on some of the most popular Linux distributions, including Debian-based systems (like Ubuntu), Fedora, and using Flatpak.

#### On Debian-based Systems (e.g., Ubuntu)

1. **Update Package List**:
   - Open a terminal and update your package list to ensure you have the latest information about available packages.
   ```bash
   sudo apt update
   ```

2. **Install Steam**:
   - Install Steam using the `apt` package manager.
   ```bash
   sudo apt install steam
   ```

3. **Launch Steam**:
   - Once the installation is complete, you can launch Steam from your application menu or by running the following command in the terminal:
   ```bash
   steam
   ```

#### On [[Fedora]]

1. **Enable the RPM Fusion Repository**:
   - Steam is available in the RPM Fusion repository, which you need to enable first.
   ```bash
   sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
   ```

2. **Install Steam**:
   - Install Steam using the `dnf` package manager.
   ```bash
   sudo dnf install steam
   ```

3. **Launch Steam**:
   - Once the installation is complete, you can launch Steam from your application menu or by running the following command in the terminal:
   ```bash
   steam
   ```

#### On OSTree-based Systems (e.g., [[Fedora Silverblue - Immutable and Container-Friendly]])

1. **Install Steam Using rpm-ostree**:
   - Use the `rpm-ostree` command to install Steam.
   ```bash
   sudo rpm-ostree install steam
   ```

2. **Reboot Your System**:
   - Reboot your system to apply the changes.
   ```bash
   systemctl reboot
   ```

3. **Launch Steam**:
   - Once your system has rebooted, you can launch Steam from your application menu or by running the following command in the terminal:
   ```bash
   steam
   ```

#### Using [[Flatpak - A Universal Packaging System for Linux]]

1. **Install Flatpak**:
   - Ensure that Flatpak is installed on your system. You can usually install it from your distribution's package manager.

   **For Debian-based systems**:
   ```bash
   sudo apt install flatpak
   ```

   **For Fedora**:
   ```bash
   sudo dnf install flatpak
   ```

2. **Add the Flathub Repository**:
   - Add the Flathub repository to your system to access its collection of Flatpak applications.
   ```bash
   flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
   ```

3. **Install Steam via Flatpak**:
   - Install Steam from the Flathub repository.
   ```bash
   flatpak install flathub com.valvesoftware.Steam
   ```

4. **Launch Steam**:
   - Once the installation is complete, you can launch Steam using the Flatpak command or through your desktop environment's application menu.
   ```bash
   flatpak run com.valvesoftware.Steam
   ```

### Running Steam

After installing Steam using any of the methods above, you can run Steam by launching it from your application menu or by using the appropriate command in the terminal (`steam` for native installations or `flatpak run com.valvesoftware.Steam` for Flatpak installations). When you first launch Steam, it will update itself and prompt you to log in with your Steam account. If you don't have an account, you can create one.

### Conclusion

Steam is readily available on Linux and can be installed using various methods depending on your Linux distribution. Whether you use a Debian-based system, Fedora, or prefer the universal Flatpak method, you can easily install and run Steam to access a wide range of games. By following the steps outlined above, you'll be able to enjoy gaming on your Linux system with Steam.