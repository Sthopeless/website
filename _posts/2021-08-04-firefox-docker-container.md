---
layout: post
title: "FireFox Docker Container"
author: sthope
image: "firefox.png"
categories: [ Docker, Portainer, Stack, LinuxServer ]
comments: true
logo: "/assets/images/doublecommander.png"
stack: "https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/firefox.yml"
---

<h2><a href="{{page.stack}}" target="_blank">Portainer Stack</a></h2>
```
---
version: "3.8"
services:
  firefox:
    image: ghcr.io/linuxserver/firefox:latest
    container_name: firefox
    network_mode: bridge
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Amsterdam
    volumes:
      - firefox_config:/config
    ports:
      - 48313:3000
    shm_size: "1gb"
    restart: unless-stopped
    labels:
      - com.centurylinklabs.watchtower.enable=true

volumes:
    firefox_config:
        external: false
```
<br>
<br>
### Deploy directly from Git Repository
<br>
Use `Repository URL`:
```
https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/firefox.yml
```
<br>
<br>
And `Compose path`:
```
firefox.yml
```
<br>
<br>
![stack](/assets/images/firefox_stack.png)
<br>
<br>
Firefox should now be available at:
```
http://firefox_IP:48313
```