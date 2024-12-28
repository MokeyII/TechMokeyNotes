---
title: Setting Up a Secure Reverse Proxy with Nginx Proxy Manager and Cloudflare
date: 2024-12-14
tags:
  - Nginx
  - Proxy
  - Manager
  - Cloudflare
  - Reverse
  - Proxmox
  - SSL
  - Certificates
  - Networking
categories:
  - Networking
  - Linux Administration
  - Virtualization
author: TheTechMokey
summary: A comprehensive guide on setting up Nginx Proxy Manager on Proxmox with Cloudflare integration, focusing on SSL certificates and secure LAN access.
features:
  - Use Nginx Proxy Manager in Proxmox for a lightweight and secure reverse proxy setup.
  - Automate SSL certificate management with Cloudflare API and Let's Encrypt.
  - Simplify internal LAN encryption using wildcard subdomains and DNS configuration.
related_links:
  - "Nginx Proxy Manager Official Guide: https://nginxproxymanager.com/guide/"
  - "Proxmox VE Scripts: https://community-scripts.github.io/ProxmoxVE/scripts?id=nginxproxymanager"
  - "Cloudflare API Documentation: https://developers.cloudflare.com/api/"
  - "Let's Encrypt SSL Certificates: https://letsencrypt.org/"
  - "Cloudflare Dashboard: https://dash.cloudflare.com/"
---


> [!NOTE] Assumptions
> - Cloudflare Domain Name purchased
> - Using [Nginx Proxy Manager LXC](https://community-scripts.github.io/ProxmoxVE/scripts?id=nginxproxymanager) in a Proxmox Virtual Environment (PVE)
> - Basic understanding of Linux Debian distro and PVE
> - DNS Server configured (UDM Pro in this case)

For additional reference, view the [Official Guide | Nginx Proxy Manager](https://nginxproxymanager.com/guide/).
# Introduction 
There are many methods to achieve encryption across your LAN. This guide focuses on a lightweight and straightforward method using Nginx Proxy Manager (NPM).

## How does this work? 

Your client or stub resolver queries the `service.domain`, which your internal DNS record points to an internal proxy server. The proxy server connects to Cloudflare on behalf of the client, retrieves content, repackages it, and delivers it back to the client.

Think of it as "DoorDash for Cloudflare," delivering certificates securely.

# Install Nginx Proxy Manager LXC
Open your PVE node's terminal. 
Install [Nginx Proxy Manager LXC](https://community-scripts.github.io/ProxmoxVE/scripts?id=nginxproxymanager)

Run the following command to install NPM:
```bash
bash -c "$(wget -qLO - https://github.com/community-scripts/ProxmoxVE/raw/main/ct/nginxproxymanager.sh)"
```

# Change Interface addresses
After installation, assign a static IPv4 and/or IPv6 prefix to the container.

```bash
sudo nano /etc/network/interfaces`
```

Example configuration:
```json
auto ens33
iface ens33 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.1

iface ens33 inet6 static
    address 2001:db8::1
    netmask 64
    gateway 2001:db8::1ead:ed:beef
```

Restart the network service:
```bash
sudo systemctl restart networking
```

# Access the Web Interface
Once you've done this, you should be able to access the web interface of your Nginx Proxy Manager
If you cannot, you can use `ss -tulnet` to view the connections  and look for `cgroup:/system.slice/openresty.service <-> ` or `cgroup:/system.slice/openresty.service v6only:1 <->`
```bash
root@nginxproxymanager:~# ss -tulnet
Netid   State    Recv-Q   Send-Q      Local Address:Port       Peer Address:Port   Process                                                                            
tcp     LISTEN   0        100             127.0.0.1:25              0.0.0.0:*       ino:4603203 sk:2 cgroup:/system.slice/system-postfix.slice/postfix@-.service <->  
tcp     LISTEN   0        511               0.0.0.0:443             0.0.0.0:*       ino:4602499 sk:3 cgroup:/system.slice/openresty.service <->                       
tcp     LISTEN   0        511               0.0.0.0:81              0.0.0.0:*       ino:4602501 sk:4 cgroup:/system.slice/openresty.service <->                       
tcp     LISTEN   0        511               0.0.0.0:80              0.0.0.0:*       ino:4602497 sk:5 cgroup:/system.slice/openresty.service <->                       
tcp     LISTEN   0        100                 [::1]:25                 [::]:*       ino:4603204 sk:6 cgroup:/system.slice/system-postfix.slice/postfix@-.service v6only:1 <->
tcp     LISTEN   0        511                  [::]:443                [::]:*       ino:4602500 sk:7 cgroup:/system.slice/openresty.service v6only:1 <->              
tcp     LISTEN   0        4096                    *:22                    *:*       ino:4602255 sk:8 cgroup:/init.scope v6only:0 <->                                  
tcp     LISTEN   0        511                  [::]:81                 [::]:*       ino:4602502 sk:9 cgroup:/system.slice/openresty.service v6only:1 <->              
tcp     LISTEN   0        511                  [::]:80                 [::]:*       ino:4602498 sk:a cgroup:/system.slice/openresty.service v6only:1 <->              
tcp     LISTEN   0        511                     *:3000                  *:*       ino:4602789 sk:b cgroup:/system.slice/npm.service v6only:0 <->                    
```
From here we can see it is listening on `:443`, `:80`, and `:81`

Navigate to `http://SERVER_IP:81` in your browser.

Login with the following:
```
Email:    admin@example.com
Password: changeme
```

Change your email and password.

# Setting up your Cloudflare API

> [!NOTE] Example
> - We are going to use `*.lan.thetechmokey.com` for this example.
> - `*` Wildcard subdomain.
> - `lan` Indicates Local Area Network, not public-facing. Other examples are `in`, `inside`, `local`, `lan`
> - `thetechmokey.com` Registered domain on Cloudflare.
> - This example is used for multiple deployments so we do not have to manually import certs all the time.

# Create your Cloudflare API Key
Navigate to your domain in the Cloudflare dashboard.

Click **Get your API Token** or **Create API Token**.

![[Pasted image 20241214020315.png]]

## Create a Token

![[Pasted image 20241214020513.png]]
## Create a custom token

![[Pasted image 20241214020630.png]]
## Set Permissions
**Permissions**: Zone → DNS → Edit.
**Zone Resources**: Include Specific Zone → Your Domain.
Continue to Summary

![[Pasted image 20241214021208.png]]
## Copy the Token

![[Pasted image 20241214021602.png]]

# Add the Let's Encrypt SSL Certificate

![[Pasted image 20241214022000.png]]

## Select Let's Encrypt

![[Pasted image 20241214022228.png]]

## Fill out the information.
Replace `0123456789abcdef0123456789abcdef01234567` with the token you copied in the last step

![[Nginx-reverse-proxy-add-LECert.png|350]]

You should see a cert populate in the SSL certificates

![[Pasted image 20241214022335.png]]


> [!NOTE] NOTE
> 


# Create a Proxy Host
Add a new proxy host in NPM:
Make sure the forward port matches that of your server. 
Such as the app ActualBudget, it's default port is `5006` so I would forward this to port `5006` rather than port `80`.

![[Pasted image 20241214022728.png]]
## Assign the Let's Encrypt certificate created earlier.

![[Pasted image 20241214022905.png]]
Click Save

The new proxy host will appear in the list.

> [!NOTE] IPv6
> - When creating an IPv6 forward, you need to put the prefix in brackets.
> - If you want to validate in a browser, you will also type in the address the same way 
> - `https://[IPV6PREFIXADDRESS]:80`


![[Pasted image 20241214023209.png]]

# Configure DNS
On your DNS server (e.g., UDM Pro), create an **A Record** (IPv4) or **AAAA Record** (IPv6):
`hostname.domain.com` → Proxy server IP.

![[Pasted image 20241214024330.png]]
Save the record

Access the service via `https://hostname.domain.com`.


![[Pasted image 20241214024624.png]]

# Finished
> [!NOTE] # Some additional Notes:
> - ## Reverse Proxy Handling SSL Termination:
> 	- HTTPS between the reverse proxy and clients is sufficient for secure internal LANs.
> 	- Backend servers can use HTTP for simpler configurations.
> - ## Certificates on the backend of servers:
> 	- Use self-signed or Cloudflare Origin Certificates for HTTPS between the reverse proxy and backend servers if required.
