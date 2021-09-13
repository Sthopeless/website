---
layout: post
title: "Portainer Stacks"
description: "Install Docker containers using docker-compose files with Portainer Stacks."
author: sthope
image: portainer-logo.png
categories: [ Ubuntu, Linux ]
pic01: "/assets/images/portainer_stacks/1.jpg"
pic02: "/assets/images/portainer_stacks/2.jpg"
pic03: "/assets/images/portainer_stacks/3.jpg"
pic04: "/assets/images/portainer_stacks/4.jpg"
pic05: "/assets/images/portainer_stacks/5.jpg"
pic06: "/assets/images/portainer_stacks/6.jpg"
pic07: "/assets/images/portainer_stacks/7.jpg"
pic08: "/assets/images/portainer_stacks/8.jpg"
pic09: "/assets/images/portainer_stacks/9.jpg"
pic10: "/assets/images/portainer_stacks/10.jpg"
pic11: "/assets/images/portainer_stacks/11.jpg"
pic12: "/assets/images/portainer_stacks/12.jpg"
pic13: "/assets/images/portainer_stacks/13.jpg"
pic14: "/assets/images/portainer_stacks/14.jpg"
pic15: "/assets/images/portainer_stacks/15.jpg"
stack_example: "https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/libreoffice.yml"
comments: true
---
### Installling Portainer

There are a few ways of running docker containers, it should not matter which way your prefer most.
Here are some examples

via Terminal, open the terminal and enter:
```
docker volume create portainer_data; \
docker run -d \
-p 8000:8000 \
-p 9000:9000 \
--name=portainer \
--restart=always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data \
--labels com.centurylinklabs.watchtower.enable=true \
--network_mode=bridge \
portainer/portainer-ce:latest
```
<br>
<br>
via docker-compose.yml file
Create `docker-compose.yml` file, eg: `nano ~/docker/docker-compose.yml` and paste:

```
---
version: "3.8"
services:
  portainer:
    container_name: "portainer"
    image: "portainer/portainer-ce:latest"
    restart: "always"
    network_mode: "bridge"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
      - "portainer_data:/data"
    port:
      - "8000:8000"
      - "9000:9000"
    labels:
      - "com.centurylinklabs.watchtower.enable=true"

volumes:
    portainer_data:
        external: false
```

<br>
### Portainer WebUI

Portainer should now be available at: http://IP:9000.<br>

1. Configure `Username` and `Password` to `Create user`.
![]({{page.pic01}})<br>
2. Select `Docker` and `Connect`.
![]({{page.pic02}})<br>
3. Click in `local` to access your instance.
![]({{page.pic03}})<br>
4. Navigate to `Endpoints` on the left-side menu and click on `local` to edit.
![]({{page.pic04}})<br>
5. In `Public IP` put the IP address of Portainer. Bonus you can name it differently if you want. After `Public IP` configured press `Update Endpoint`.
![]({{page.pic05}})<br>
6. Navigate to `Stacks` on the left-side menu.
![]({{page.pic06}})<br>
7. Here you can paste most docker-compose.yml files or create your own.
![]({{page.pic07}})<br>
8. For example:
![]({{page.pic08}})<br>
9. Here you can upload Stacks directly from Github, Gitea and many others. 
![]({{page.pic10}})<br>
10. Here is a example using [this personal Gitea server]({{page.stack_example}}).
![]({{page.pic11}})<br>
11. Stack running
![]({{page.pic12}})<br>
12. Inside the `Stack`
![]({{page.pic13}})<br>
13. Updating/Editing the `Stack` locally.
![]({{page.pic14}})<br>
14. Stack file can also be edited on Git and pushed again to assume the changes.
![]({{page.pic15}})<br>

