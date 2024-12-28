---
title: "YUM: The Yellowdog Updater, Modified"
date: 2024-12-13
tags:
  - Linux
  - Package Management
  - YUM
categories:
  - Linux Basics
  - System Administration
author: "TheTechMokey"
summary: "Explore YUM, the package manager for RPM-based distributions like Fedora, its key functions, advantages, and its transition to DNF."
features:
  - Automatic dependency resolution for seamless package installations.
  - Comprehensive repository and group management.
  - Extensible through plugins for added functionality.
related_links:
  - "YUM Documentation: https://yum.baseurl.org/"
  - "Transition to DNF: https://dnf.readthedocs.io/"
  - "Fedora Project: https://getfedora.org/"
---

### YUM (Yellodog Updater, Modified):

**YUM (Yellowdog Updater, Modified)** is a package management utility for RPM-based distributions like [[Fedora]]. It simplifies the process of installing, updating, and removing software packages, and it handles dependencies automatically.

### Key Functions of YUM:

1. **Package Installation**:
    
    - Allows users to install new software packages from [[Fedora]] repositories.
    - Example command: `yum install package_name`
2. **Package Removal**:
    
    - Enables users to remove installed software packages.
    - Example command: `yum remove package_name`
3. **Package Updates**:
    
    - Facilitates updating installed packages to their latest versions.
    - Example command: `yum update`
4. **Dependency Resolution**:
    
    - Automatically resolves and installs package dependencies.
    - Ensures that all required libraries and dependencies are installed.
5. **Repository Management**:
    
    - Manages software repositories from which packages are downloaded.
    - Allows adding, removing, and configuring repositories.
6. **Package Search**:
    
    - Provides functionality to search for packages in the repositories.
    - Example command: `yum search package_name`
7. **Group Management**:
    
    - Allows users to install or remove groups of packages.
    - Example command: `yum groupinstall "Group Name"`

### Advantages of YUM:

- **Automatic Dependency Resolution**: Simplifies the installation process by automatically handling dependencies.
- **Repository Management**: Easily manages multiple repositories, allowing users to add or remove them as needed.
- **Extensibility**: Supports plugins to extend its functionality.
- **Command-Line Interface**: Provides a powerful CLI for advanced users and system administrators.

### Limitations of YUM:

- **Performance**: YUM can be slower compared to newer package managers like DNF.
- **Dependency Management**: While effective, YUM's dependency resolution is not as advanced as DNF's.

### Transition to DNF:

Fedora has transitioned from YUM to [[DNF (Dandified YUM) - Fedora's Advanced Package Manager]] as the default package manager starting from Fedora 22. [[DNF (Dandified YUM) - Fedora's Advanced Package Manager]] was introduced to address some of the limitations of YUM, offering improved performance, better dependency management, and a more user-friendly experience.

### Conclusion:

YUM has been a reliable package manager for RPM-based distributions like Fedora, providing essential functions for installing, updating, and managing software packages. While it has been largely replaced by DNF in recent [[Fedora]] releases, YUM played a crucial role in the evolution of package management in Fedora.