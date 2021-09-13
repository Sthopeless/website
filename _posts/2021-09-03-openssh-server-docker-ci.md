---
layout: post
title: "Openssh-server Docker Container"
description: ""
author: sthope
image: 
categories: [ Docker, Portainer, SSH ]
comments: true
---

First create openssh-server configuration folders:
```
mkdir -p ~/docker/openssh-server/{config,ssh}
```
<br>

Portainer Stack:
```yaml
---
version: "3.8"
services:
  openssh-server:
    image: ghcr.io/linuxserver/openssh-server:latest
    container_name: openssh-server
    hostname: my_server
    environment:
      - PUID=1000 
      - PGID=1000
      - TZ=Europe/Amsterdam
      - DOCKER_MODS=linuxserver/mods:openssh-server-rsync|linuxserver/mods:openssh-server-openssh-client|linuxserver/mods:openssh-server-git
      - PUBLIC_KEY_FILE=~/docker/openssh-server/ssh
      - PASSWORD_ACCESS=false
      - SUDO_ACCESS=true
    volumes:
      - ~/docker/openssh-server/config:/config
      - ~/docker/openssh-server/ssh:/root/.ssh
      - ~/docker:/my_server
    ports:
      - 2222:2222
    restart: unless-stopped
```

After is running configure your ssh keys, you can generate new ones with command:
```
docker run --rm -it --entrypoint /keygen.sh linuxserver/openssh-server
```

And after keys are configured you can ssh with:
```
ssh -i /root/.ssh/your_key -p PORT USERNAME@IP
```

And from your Docker terminal you can enter the container with:
```
docker exec -it openssh-server /bin/bash
```
