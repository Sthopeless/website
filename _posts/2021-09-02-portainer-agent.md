---
layout: post
title: "Portainer Agent"
description: "Connection multiple Docker Hosts in one Portainer instance"
author: sthope
image: 
categories: [ Docker, Portainer, Portainer Agent ]
comments: true
pic01: "/assets/images/portainer-agent/1.jpg"
pic02: "/assets/images/portainer-agent/2.jpg"
pic03: "/assets/images/portainer-agent/3.jpg"
pic04: "/assets/images/portainer-agent/4.jpg"
---
# Portainer Edge Agent

<br>
Open `Endpoints` tab on Portainer:
```
http://Portainer_IP:9000/#!/endpoints
```

![pic01]({{page.pic01}})
<br>
1. Select `Edge Agent`.
2. Give it a `Name` (generally hostname of the instance you are adding).
3. `Portainer server URL` is the url of your Portainer: http://Portainer_IP:9000
![pic02]({{page.pic02}})
<br>
<br>
Copy `EDGE_ID` and `EDGE_KEY`
![pic03]({{page.pic03}})
![pic04]({{page.pic04}})
<br>
On the terminal of host you are going to add to Portainer send:
```
bash -c "$(wget -qLO - https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/raw/branch/master/portainer/install-portainer-agent)" EDGE_ID EDGE_KEY
```
Replace `EDGE_ID` and `EDGE_KEY` with ones given by Portainer 

