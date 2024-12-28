---
title: "KDE Rounded Corners: Build and Customize Rounded Corners for KDE"
date: 2024-12-13
tags:
  - KDE
  - Linux
  - Desktop Customization
  - Open Source
categories:
  - Guides
  - Customization
  - Development
summary: "A step-by-step guide to building and customizing KDE Rounded Corners, including instructions for installation, updates, and troubleshooting."
author: "TheTechMokey"
notes:
  - "This guide explains how to build and customize the KDE Rounded Corners effect from source for various distributions."
  - "The guide includes auto-rebuild instructions after KWin updates."
sources:
  - "https://github.com/matinlotfali/KDE-Rounded-Corners"
  - "https://invent.kde.org/plasma/kwin/-/issues/198"
warnings:
  - "Ensure you install the required development packages for your Linux distribution."
  - "The effect must be rebuilt after each KWin update unless auto-rebuild is configured."
---


# KDE-Rounded-Corners
![[github-mark-white.svg|18]] https://github.com/matinlotfali/KDE-Rounded-Corners/tree/master

# How to build from source code:

You need to install development packages for your distribution first:

<details>
<summary>Debian based (Ubuntu, Kubuntu, KDE Neon)</summary>
<br>
    
Plasma 5 - by [alex47](https://github.com/alex47):
```   
sudo apt install git cmake g++ extra-cmake-modules kwin-dev libkf5configwidgets-dev 
```
Plasma 6

```
sudo apt install git cmake g++ extra-cmake-modules kwin-dev qt6-base-dev-tools kf6-kcmutils-dev
```

</details>
<details>
<summary>Fedora</summary>
<br>

Plasma 5 (Fedora 39)
   ```bash
   sudo dnf install git cmake gcc-c++ extra-cmake-modules kwin-devel kf5-kconfigwidgets-devel libepoxy-devel
   ```
 Plasma 6 (Fedora 40 and later)
   ```bash
   sudo dnf install git cmake gcc-c++ extra-cmake-modules kwin-devel kf6-kconfigwidgets-devel libepoxy-devel kf6-kcmutils-devel qt6-qtbase-private-devel wayland-devel
   ```
</details>
<details>
<summary>Arch - by https://github.com/hexa-one</summary>

  ```
  sudo pacman -S git cmake extra-cmake-modules base-devel
  yay -S qt5-tools
  ```
  or AUR package by [xiota](https://aur.archlinux.org/account/xiota)  
  ```
  sudo pamac build kwin-effect-rounded-corners-git
  ```
</details>
<details>
<summary>OpenSUSE - by https://github.com/mathiasgredal, https://github.com/Richardsause, and https://github.com/aaronkirschen</summary>
<br>

 - Plasma 5 (by https://github.com/mathiasgredal, https://github.com/Richardsause)
  ```
  sudo zypper install git cmake gcc-c++ extra-cmake-modules libqt5-qttools-devel kconfigwidgets-devel kwindowsystem-devel kguiaddons-devel ki18n-devel knotifications-devel kwin5-devel libQt5Gui-devel libQt5OpenGL-devel libepoxy-devel libqt5-qtnetworkauth-devel
  ```
 - Plasma 6 (by https://github.com/aaronkirschen)
  ```
  sudo zypper in git cmake gcc-c++ kf6-kconfigwidgets-devel kf6-kcmutils-devel kwin6-devel kf6-kwindowsystem-devel qt6-quick-devel qt6-core-private-devel
  ```
</details>
<details>
<summary>Void - by https://github.com/lay-by</summary>

  ```
  xbps-install git cmake make qt5-tools-devel extra-cmake-modules gettext-devel kwin-devel
  ```
</details>
<details>
<summary>NixOS - by https://github.com/flexagoon</summary>

   ```
   nix-env -iA nixos.kde-rounded-corners
   ```
</details>

Then clone the source code and compile it:
```bash
git clone https://github.com/matinlotfali/KDE-Rounded-Corners
cd KDE-Rounded-Corners
mkdir build
cd build
cmake ..
cmake --build . -j
sudo make install
```

# Load & Unload

To activate the effect, you can now log out and log back in, or run the command below inside the `build` directory:
```bash
sh ../tools/load.sh
```

To fully uninstall the effect, run the following commands inside the `build` directory:

```bash
sh ../tools/unload.sh
sudo make uninstall
```

# Auto install after KWin update

After each `kwin` package update, the effect becomes incompatible. So it won't load without a rebuild.

As long as the effect is not part of the `kwin` yet (being discussed 
[here](https://invent.kde.org/plasma/kwin/-/issues/198)), you can automate the re-installation by running the command
below inside the `build` directory:

```bash
sh ../tools/install-autorun-test.sh
```

The command above adds a `desktop` file inside the `autorun` directory which checks if the effect is still supported,
if it is not supported, it will automatically rebuild and reinstall the effect.

> [!NOTE]
> The script uses `qdbus` to show a progress bar. On Plasma 6, it is not installed by default. You need to manually install the package `qtchooser`.

# Settings

You can change the corner radius, or disable the effect in:

> [ System Settings ] --> [ Workspace Behavior ] --> [ Desktop Effects ] --> [ ShapeCorners ]

# Tips

## Disable conflicting native window outline

If using Breeze (default) window decorations with Plasma 5.27 or higher you may wish to disable the native window outline, to prevent it from overlapping and causing visual glitches.

- System settings -> Themes -> Window Decorations -> Breeze -> Edit icon -> Shadows and Outline tab -> Outline intensity (Off)

## Add shadow to windows without decoration (like Steam)

You can add shadows for specific windows using the hack below. I don't know how to enforce it in my code.

1. In [ System settings ] -> [ Window management ] -> [ Window rules ] -> [ Appearance & Fixes ]:

   **Add [steam] and set [ No titlebar ] and frame to [ No ]**
   
2. In [ System settings ] -> [ Application Style ] -> [ Window decoration ] -> [ Breeze theme setting ] -> [ Window specific overrides ]:

   **Add [steam] and set [ Hide Window title bar ] to [ Yes ].**

After that, the Steam window gets its shadows back.

## Add Debug Messages

When troubleshooting or reporting an issue, it might be useful to enable Debug logs during the build time using:

```bash
cmake .. --DCMAKE_BUILD_TYPE=Debug
cmake --build . -j
```

After the installation and loading the effect, debug messages would appear in `journalctl`:

```bash
journalctl -f | grep kwin
```

or have some colorful logs with

```bash
sh ../tools/show-kwin-logs.sh
```