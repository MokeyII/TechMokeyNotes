---
title: Installing Docker
date: 2024-12-13
tags:
  - Docker
  - Debian
  - Installation
  - DevOps
categories:
  - Guides
  - Linux
  - Software Installation
summary: Step-by-step guide to installing Docker on Debian, including commands for setting up the repository, adding the GPG key, and validating the installation.
author: TheTechMokey
---

# Debian/Unbuntu
Update package list
```bash
sudo apt update
```

Install packages
```bash
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release software-properties-common
```

Add Docker's GPG Key
```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Docker repo setup
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine
```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
```

Validate installation and version
```bash
docker --version
docker run hello-world
```

(Docker should come with Docker Compose, if not)
```bash
sudo apt install docker-compose-plugin
```

