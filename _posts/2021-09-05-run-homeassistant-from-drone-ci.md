---
layout: post
title: "Home Assistant & Drone CI"
description: "Run Home Assistant from Drone CI"
author: sthope
image: 
categories: [ Docker, Drone, Gitea, Git ]
comments: true
---

Create a git repository connected and enabled in Drone CI and paste this into `.drone.yml`:
```yaml
kind: pipeline
step: default

steps:
  - name: ha
    image: ghcr.io/home-assistant/home-assistant:stable
    network_mode: host
    environment:
      TZ: Europe/Amsterdam
    
services:
  - name: homeassistant
    image: ghcr.io/home-assistant/home-assistant:stable
    network_mode: host
```
After pulling the images Home Assistant should be available at `http://IP:8123`

Official available images:
- [stable](ghcr.io/home-assistant/home-assistant:stable)
- [dev](ghcr.io/home-assistant/home-assistant:dev)
- [rc](ghcr.io/home-assistant/home-assistant:rc)
- [beta](ghcr.io/home-assistant/home-assistant:beta)
- [latest](ghcr.io/home-assistant/home-assistant:latest)

