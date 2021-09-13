---
layout: post
title: "Docker Portainer"
description: "Docker Portainer"
author: sthope
image: "portainer-small-logo.png"
categories: [ Docker, Portainer ]
comments: true
---

# Portainer

1. On the terminal create folder for Portainer, eg:  

```
mkdir -p /docker/portainer
```

2. Create and start the container:  

```
docker run -d \
-p 8000:8000 \
-p 9000:9000 \
--name=portainer \
--restart=always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /docker/portainer:/data \
portainer/portainer-ce:latest
```

3. Open WebUI at:  

```http
http://{IP}:9000
```

4. Create new User
<img src="/assets/images/docker-portainer/1.jpg" width="85%" height="85%">

5. Choose Docker
<img src="/assets/images/docker-portainer/2.jpg" width="85%" height="85%">

6. Select your instance
<img src="/assets/images/docker-portainer/3.jpg" width="85%" height="85%">

7. Open Endpoints and setup the host IP
<img src="/assets/images/docker-portainer/4.jpg" width="85%" height="85%">  

<img src="/assets/images/docker-portainer/5.jpg" width="85%" height="85%">


