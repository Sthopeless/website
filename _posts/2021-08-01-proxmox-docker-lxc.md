---
layout: post
title: "Proxmox Docker LXC"
description: "Installing on Proxmox a Linux Container with Docker installed and Portainer, VScode and Watchtower container configured, all with 1 line command."
author: sthope
categories: [ Docker, Proxmox, Portainer ]
image: "proxmox-small-logo.png"
comments: true
---

# Setup the LXC

- In the terminal of Proxmox enter:

```
clear; bash -c "$(wget -qLO - https://git.sthopeless.com/sthope/proxmox_portainer/raw/branch/master/create_container.sh)"

```

It will configure and start a Debian LXC. After created you can rename the LXC and give it a static IP.

<br>
# LXC configuration
- In the LXC terminal setup root password with 

```
passwd
```

<br>
### Finish

- Portainer should be running at:

```http
http://{IP}:9000
```
- VSCode should be running at:

```http
http://{IP}:8443
```
- WatchTower for auto updating the containers is also installed and if you want new containers to use it simply add the label:

```
com.centurylinklabs.watchtower.enable=true
```
