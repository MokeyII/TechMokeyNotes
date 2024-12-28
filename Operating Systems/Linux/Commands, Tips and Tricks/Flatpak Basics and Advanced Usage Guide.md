---
title: "Flatpak Basics and Advanced Usage Guide"
date: 2024-09-25
tags:
  - Linux
  - Flatpak
  - Package Management
  - Software Deployment
categories:
  - Guides
  - Linux
  - Tools
summary: "A comprehensive guide to using Flatpak, including installation, management, and advanced tips for configuring custom installations and using Flatpak Builder."
author: "TheTechMokey"
notes:
  - "Flatpak allows sandboxed application management across various Linux distributions."
  - "Includes instructions for managing Flatpak remotes, building applications, and handling custom installations."
sources:
  - "https://flathub.org"
  - "https://flathub.org/setup"
warnings:
  - "Ensure sufficient disk space for Flatpak applications, especially when using custom installations."
  - "Use remotes cautiously to avoid conflicts or security issues."
---


*Created on 09-21-2024 @ 22:00am EST*
*Modified on 09-25-2024 @ 10:14 EST*

--- 
Flathub site: https://flathub.org
Setup Guide: https://flathub.org/setup
# Identifier Formats
### ID
```
<ending>.<organization>.<name>
```
---
### ID + Architecture + Branch
```
<ID>/<arch>/<branch>
```
---
### ID + branch
```
<ID>//<branch>
```
---
### ID + architecture
```
<ID>/<arch>//
```

# Basic Commands
### Install
```bash
flatpak install <remote> <ID>
```
Example:
```bash
flatpak install flathub org.gimp.GIMP

```
```bash
flatpak install <path-to-flatpakref>
```
Example:
```bash
flatpak install /path/to/application.flatpakref
```

---
### Uninstall
```bash
flatpak uninstall <ID>
```
Example:
```bash
flatpak uninstall org.gimp.GIMP
```

---
### Run
```bash
flatpak run <ID>
```
Example:
```bash
flatpak run org.gimp.GIMP
```

---
### Update
```bash
flatpak update
```
---
# Remotes
### Search all remotes
```bash
flatpak search <term>
```
### List configured remotes
```bash
flatpak remotes
```
---
### Add a remote
```bash
flatpak remote-add <remote-name> <URL>
```
*Use --if-not-exists to avoid errors.*
Example:
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

---
### Remove a remote
```bash
flatpak remote-delete <remote-name>
```
Example:
```bash
flatpak remote-delete flathub
```

---
### List remote contents
```bash
flatpak remote-ls <remote-name>
```
Example:
```bash
flatpak remote-ls flathub
```
---
# Flatpak Builder

|     |     |
| --- | --- |
| Command Format     |  `flatpak-builder <build-dir> <manifest>`   |

---
|     |     |
| --- | --- |
| **Definitions** | 
| `<build-dir>` | Directory where build stuff happens |
| `<Manifest>` | Path to Manifest file |

---
|     |     |
| --- | --- |
| **Options** | |
| `--repo=<repo-name>` | Export to a specified repository |
| `--install` | Install the build result, if it succeeds |
| `--install-deps-from=<remote>` | Install build dependencies from a specified remote |

Examples:
Build an application
```bash
flatpak-builder --repo=my-repo --install /path/to/build-dir /path/to/manifest.json
```

Export to a specified respository
```bash
flatpak-builder --repo=my-repo /path/to/build-dir /path/to/manifest.json
```

Install build dependencies from a specified remote
```bash
flatpak-builder --install-deps-from=flathub /path/to/build-dir /path/to/manifest.json
```

# Example of searching, removing and installing a Flatpak package via Terminal
```bash
mokey@frigg:~$ flatpak list  
Name                                                Application ID                                               Version                                Branch                   Installation  
... OUTPUT OMMITED ...
Visual Studio Code                                  com.visualstudio.code                                        1.93.1                                 stable                   system  
... OUTPUT OMMITED ...
mokey@frigg:~$ flatpak uninstall com.visualstudio.code  

       ID                           Branch        Op  
1. [-] com.visualstudio.code        stable        r  
  
Uninstall complete.  
mokey@frigg:~$ flatpak search vscodium  
Name                          Description                           Application ID                        Version                       Branch          Remotes  
VSCodium                      Telemetry-less code editing           com.vscodium.codium                   1.93.1.24256                  stable          flathub  
VSCodium - Insiders           Telemetry-less code editing           com.vscodium.codium-insiders          1.93.0.24242-insider          stable          flathub  
mokey@frigg:~$ flatpak install flathub com.vscodium.codium  
Looking for matches…  
  
com.vscodium.codium permissions:  
   ipc      network      fallback-x11      pulseaudio      ssh-auth      wayland      x11      devices      devel     file access [1]     dbus access [2]     system dbus access [3]  
  
   [1] host, xdg-config/kdeglobals:ro, xdg-run/gnupg:ro  
   [2] com.canonical.AppMenu.Registrar, org.freedesktop.Flatpak, org.freedesktop.secrets, org.kde.kwalletd5  
   [3] org.freedesktop.login1  
  
  
       ID                           Branch          Op         Remote          Download  
1. [✓] com.vscodium.codium          stable          i          flathub         115.3 MB / 135.0 MB  
  
Installation complete.
```

# Tips and Tricks for Flatpak
## Adding a custom installation

By default Flatpak installs apps system-wide, and can also be made to install per-user with the `--user` option accepted by most commands. A third option is to set up a custom installation, which could be stored on an external hard drive.

First ensure that the config directory exists:

```bash
$ sudo mkdir -p /etc/flatpak/installations.d
```

Then open a file in that directory as root:

```bash
# nano /etc/flatpak/installations.d/extra.conf
```

And write something like this:

```
[Installation "extra"]
Path=/run/media/mwleeds/ext4_4tb/flatpak/
DisplayName=Extra Installation
StorageType=harddisk
```

See [flatpak-installation(5)](https://docs.flatpak.org/en/latest/flatpak-command-reference.html#flatpak-installation) for the full format specification. Replace the path with the actual path you want to use. You can use `df` to see mounted file systems and `mkdir` to create a `flatpak` directory so the path specified by `Path=` exists.

Then you can add a remote using a command like:

```bash
$ flatpak --installation=extra remote-add flathub https://flathub.org/repo/flathub.flatpakrepo
```

And install to it with:

```bash
$ flatpak --installation=extra install flathub org.inkscape.Inkscape
```

And run apps from it with:
> [!NOTE]
> If your custom installation is the only one with the app you’re running, `--installation` can be omitted.
```bash
$ flatpak --installation=extra run org.inkscape.Inkscape
```

