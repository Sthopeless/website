---
layout: post
title: "WatchTower"
description: "Docker WatchTower"
author: sthope
image: "watchtower-logo.png"
categories: [ Docker, WatchTower ]
comments: true
---

# WatchTower

1. Create and run Portainer Stack:

```yaml
---
version: "3.8"
services:
  watchtower:
    container_name: watchtower
    image: containrrr/watchtower
    restart: unless-stopped
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    environment:
      - TZ=Europe/Amsterdam
      - WATCHTOWER_CLEANUP=true
      - WATCHTOWER_POLL_INTERVAL=86400
      - WATCHTOWER_LABEL_ENABLE=true
```

