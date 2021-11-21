---
layout: post
title: "Jekyll Docker Website"
author: sthope
image: 
categories: [ Docker, Jekyll ]
comments: true
---
# Portainer Stack

```yaml
---
version: "3.8"
services:
  jekyll:
    image: "jekyll/jekyll:latest"
    container_name: "jekyll"
    hostname: "jekyll"
    command: "jekyll serve --force_polling"
    network_mode: "bridge"
    environment:
      - "TZ=Europe/Amsterdam"
    volumes:
      - "/edit/this:/srv/jekyll"
    ports:
      - "4000:4000"
    restart: "unless-stopped"

volumes:
    jekyll:
        external: false
```
Create folder with eg: ```mkdir -p ~/jekyll``` and change the Volume
# Portainer Stack with Volumes
```yaml
---
version: "3.8"
services:
  jekyll:
    image: "jekyll/jekyll:latest"
    container_name: "jekyll"
    hostname: "jekyll"
    command: "jekyll serve --force_polling"
    network_mode: "bridge"
    environment:
      - "TZ=Europe/Amsterdam"
    volumes:
      - "jekyll:/srv/jekyll"
    ports:
      - "4000:4000"
    restart: "unless-stopped"

volumes:
    jekyll:
        external: false
```
** Good for testing, not recommended for production. **

```
sudo docker exec -it jekyll /bin/sh -c 'jekyll new /srv/jekyll/ --blank --force'
```
Send this from the terminal to initiate a blank website.
