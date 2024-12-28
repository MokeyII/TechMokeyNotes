---
title: "Installing NVIDIA Drivers and Hardware Acceleration on Fedora"
date: 2024-09-17
tags:
  - Linux
  - Fedora
  - NVIDIA
  - Drivers
  - Hardware Acceleration
categories:
  - Guides
  - Fedora
  - System Optimization
summary: "Comprehensive guide to installing NVIDIA drivers, multimedia codecs, and hardware acceleration packages on Fedora, with explanations and a helpful automation script."
author: "Your Name"
notes:
  - "Secure boot must be disabled before following this guide."
  - "Be cautious with Gamemode as it may cause compatibility issues with NVIDIA drivers."
---

One of the biggest hassles with Linux are the NVIDIA Drivers. Here's how you install these drivers and the explanation of the commands for [[Fedora]] This guide will assist with installing NVIDIA drivers from a newly installed [[Fedora Workstation]].

> [!NOTE]
> This guide assumes you have secure boot disabled and have a general understating on how to navigate in [[Fedora Workstation]]

# You Can Start Installing 3rd Party Repositories with the following

```bash
sudo dnf install -y \
    https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
    https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
### Command breakdown

| Package / Command                                                                                       | Description                                                         |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm`       | free repository package for Fedora                                  |
| `\`                                                                                                     | Multi line escape character. Remember this, It does get used a lot. |
| `https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm` | non-free repository package for Fedora                              |
# Update Installed Packages to Latest Version
```bash
sudo dnf -y update
```
`y` - automatically answers **yes** to all prompts
# Quick Install Drivers and Svt Codecs
```bash
sudo dnf install -y akmod-nvidia xorg-x11-drv-nvidia-cuda xorg-x11-drv-nvidia-cuda-libs \
	nvidia-vaapi-driver libva-utils
```
## What Are These?

| Package                           | Puropose                                                                                                                                         |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **akmod-nvidia**                  | **AKMOD System**: A system that automatically builds and installs kernel modules (like the NVIDIA driver) when a new kernel is installed.        |
| **xorg-x11-drv-nvidia-cuda**      | **NVIDIA CUDA Drivers**: The proprietary NVIDIA drivers specifically tailored for CUDA (Compute Unified Device Architecture) support.            |
| **xorg-x11-drv-nvidia-cuda-libs** | **CUDA Libraries**: The necessary runtime libraries for CUDA (Compute Unified Device Architecture) applications to function with NVIDIA drivers. |
| **nvidia-vaapi-driver**           | **VA-API Integration**: Allows applications that use VA-API for hardware-accelerated video decoding and encoding to work with NVIDIA GPUs.       |
| **libva-utils**                   | **Performance Analysis**: Tool to analyze the performance of VA-API operations.                                                                  |
# Install Default Codecs
```bash
sudo dnf install ffmpeg-libs --allowerasing
```
## Command breakdown

| Command or Package                            | Purpose                                                                                                                       |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `sudo dnf install ffmpeg-libs --allowerasing` | Command to install the `ffmpeg-libs` package, allowing the erasure of conflicting packages if necessary.                      |
| `ffmpeg-libs`                                 | Libraries for FFmpeg, a comprehensive multimedia framework for handling video, audio, and other multimedia files and streams. |
| `sudo dnf groupupdate Multimedia`             | Command to update all packages in the "Multimedia" group, which includes a variety of multimedia-related software.            |
# Hardware Acceleration

```bash
sudo dnf install sox sox-plugins-nonfree svt-av1 gstreamer1-svt-av1 gstreamer1-svt-vp9 svt-vp9 libheif libheif-freeworld rav1e dav1d vkd3d-compiler
```
## Command breakdown

| Command or Package    | Purpose                                                                       |
| --------------------- | ----------------------------------------------------------------------------- |
| `sudo dnf install`    | Command to install packages using the DNF package manager on Fedora.          |
| `sox`                 | A command-line utility for audio processing.                                  |
| `sox-plugins-nonfree` | Non-free plugins for SoX, providing additional audio processing capabilities. |
| `svt-av1`             | Scalable Video Technology for AV1 encoder.                                    |
| `gstreamer1-svt-av1`  | GStreamer plugin for SVT-AV1 encoder.                                         |
| `gstreamer1-svt-vp9`  | GStreamer plugin for SVT-VP9 encoder.                                         |
| `svt-vp9`             | Scalable Video Technology for VP9 encoder.                                    |
| `libheif`             | Library for reading and writing HEIF (High Efficiency Image Format) files.    |
| `libheif-freeworld`   | Freeworld version of libheif, often including additional codecs.              |
| `rav1e`               | An AV1 encoder focused on speed and efficiency.                               |
| `dav1d`               | A fast AV1 decoder.                                                           |
| `vkd3d-compiler`      | Compiler for VKD3D, a Direct3D 12 to Vulkan translation library.              |
# Gamemode

> [!NOTE]
> There have been some reports of Gamemode breaking with Nvidia. Just be ready to remove this or attempt to fix if you encounter any issues.
> `sudo dnf remove gamemode`

```bash
sudo dnf install -y gamemode
```

What is `gamemode`?

**GameMode** is a tool developed by Feral Interactive that optimizes the system for gaming. When activated, it can:

- **Adjust CPU Governor**: Switch the CPU governor to "performance" mode to improve game performance.
-  **I/O Prioritization**: Adjust I/O priorities to favor the game.
- **GPU Performance**: Apply GPU performance tweaks.
- **Custom Scripts**: Run custom user scripts for additional optimizations.

# Media Player
You do have a few options for Media players
If you would like to install these via flatpak, check out the [[Flatpak Basics and Advanced Usage Guide]].

| Player                                                                    | Description                        |
| ------------------------------------------------------------------------- | ---------------------------------- |
| [VLC Media Player](https://flathub.org/apps/org.videolan.VLC)             | Full Feature Media Player          |
| [MPV](https://flathub.org/apps/io.mpv.Mpv)                                | The wokhorse of media players      |
| [Celluoid](https://flathub.org/apps/io.github.celluloid_player.Celluloid) | Frontend gtk (GNOME) Verion of MPV |
| [Haruna](https://flathub.org/apps/org.kde.haruna)                         | Frontend qt (KDE) version of MPV   |
# Simple Driver and Codec/Hardware Acceleration Script For Lazy people
Copy the script into a dir such as `~/Documents` and save it as `vid-hwa.sh`
run the command `chmod +x vid-hwa,sh`
execute the script with `./vid-hwa.sh`
```bash
#!/bin/bash

# Exit immediately if a command exits with a non-zero status
set -e

# Update the system
echo "Updating the system..."
sudo dnf -y update
install_packages() {
    echo "Installing packages: $@"
    sudo dnf install -y "$@"
}

# Install RPM Fusion repositories
echo "Installing RPM Fusion repositories..."
install_packages \
    https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
    https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# Install all necessary packages in one go
echo "Installing NVIDIA drivers, multimedia libraries, and related packages..."
install_packages \
    akmod-nvidia \
    xorg-x11-drv-nvidia-cuda \
    xorg-x11-drv-nvidia-cuda-libs \
    svt-av1 \
    svt-vp9 \
    nvidia-vaapi-driver \
    libva-utils \
    ffmpeg-libs --allowerasing \
    sox \
    sox-plugins-nonfree \
    gstreamer1-svt-av1 \
    gstreamer1-svt-vp9 \
    libheif \
    libheif-freeworld \
    rav1e \
    dav1d \
    vkd3d-compiler \
    gamemode

echo "Installation completed successfully."

```