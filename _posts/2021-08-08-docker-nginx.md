---
layout: post
title: "Docker NGINX"
description: "Docker NGINX & Authelia"
author: sthope
image: "nginx-logo.png"
categories: [ Docker, NGINX, LinuxServer ]
env_file: https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/nginx/nginx.env
comments: true
---

- Create a file on your PC named `nginx.env` and paste this or [download this template]( {{page.env_file}} )

```
domain=example.com
domain_subdomains=homeassistant,plex,nodered,jellyfin,sonarr,radarr
user_email=example@gmail.com
nginx_validation=dns
nginx_dnsplugin=cloudflare
#nginx_duckdnstoken=
nginx_container_name=nginx
authelia_container_name=authelia
PUID=1000
PGID=1000
TZ=Europe/Amsterdam
rst_mode=unless-stopped
maximunddb_license_key=
volume_nginx=/docker/nginx/nginx
volume_authelia=/docker/nginx/authelia
autoupdate_nginx=true
autoupdate_authelia=true
tag_nginx=latest
tag_authelia=latest
nginx_httpsPort=443
nginx_httpPort=80
```

Fill up according to your instalation

- Create and run this Portainer Stack:

```yaml
version: "3.8"

networks:
  nginx_network:
    external:
      name: nginx_network
  default:
    driver: bridge

services:
  nginx:
    image: ghcr.io/linuxserver/swag:${tag_nginx}
    container_name: ${nginx_container_name}
    cap_add:
      - NET_ADMIN
    networks:
      - nginx_network
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=${TZ}
      - URL=${nginx_domain}
      - SUBDOMAINS=${nginx_subdomains}
      - VALIDATION=${nginx_validation}
      - DNSPLUGIN=${nginx_dnsplugin}
      - EMAIL=${user_email}
      - MAXMINDDB_LICENSE_KEY=${maximunddb_license_key}
      - STAGING=false
      - ONLY_SUBDOMAINS=false
    volumes:
      - ${volume_nginx}:/config
    ports:
      - ${nginx_httpsPort}:443
      - ${nginx_httpPort}:80
    restart: ${rst_mode}
    labels:
      - com.centurylinklabs.watchtower.enable=${autoupdate_nginx}

  authelia:
    image: authelia/authelia:${tag_authelia}
    container_name: ${authelia_container_name}
    networks:
      - nginx_network
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=${TZ}
    volumes:
      - ${volume_authelia}:/config
    restart: ${rst_mode}
    labels:
      - com.centurylinklabs.watchtower.enable=${autoupdate_authelia}
```
