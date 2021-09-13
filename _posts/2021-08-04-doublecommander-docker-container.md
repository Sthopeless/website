---
layout: post
title: "Double Commander"
description: "Double Commander is a free and open-source multi-platform two-panel orthodox file manager that is inspired by the Microsoft Windows-only Total Commander."
author: sthope
image: ""
categories: [ Docker, Portainer, Stack, LinuxServer ]
comments: true
logo: "/assets/images/doublecommander.png"
doublecmd_normal: "https://doublecmd.sourceforge.io/gallery/images/MainWindow.png"
doublecmd_dark: "https://doublecmd.sourceforge.io/gallery/images/MainWindowDark.png"
---
![logo]({{page.logo}})

<h2><a href="https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/doublecommander.yml" target="_blank">Portainer Stack</a></h2>
```
---
version: "3.8"
services:
  doublecommander:
    image: ghcr.io/linuxserver/doublecommander:latest
    container_name: doublecommander
    network_mode: bridge
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Amsterdam
    volumes:
      - /docker/doublecommander:/config
      - /docker:/data
    ports:
      - 52486:3000
    restart: unless-stopped
```  
<br>
<table>
  <tr>
    <td>PUID</td>
    <td>userID check with: ID $USER</td>
  </tr>
  <tr>
    <td>PGID</td>
    <td>groupID check with: ID $USER</td>
  </tr>
  <tr>
    <td>TZ</td>
    <td>your TimeZone</td>
  </tr>
  <tr>
    <td>Volume /config</td>
    <td>DoubleCommander configs folder </td>
  </tr>
  <tr>
    <td>Volume /data</td>
    <td>Folder you want to access with DoubleCommander</td>
  </tr>
  <tr>
    <td>Port 52486</td>
    <td>http port where the container is running</td>
  </tr>
</table>
<br>
Create folder with e.g.:  
```mkdir -p /docker/doublecommander```
<br>
<br>
<br>
<br>
![dark]({{page.doublecmd_dark}})
<br>
<br>
<br>
<br>
![normal]({{page.doublecmd_normal}})
<br>
<br>
<br>
<br>