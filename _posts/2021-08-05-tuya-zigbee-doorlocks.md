---
layout: post
title: "Tuya Zigbee DoorLocks"
description: "Unlock Tuya Zigbee Doorlocks using the API"
author: sthope
image: "tuya-logo.png"
categories: [ Tuya, Zigbee, Docker ]
tyfiles: https://git.sthope.dev/sthope/Tuya_Zigbee_DoorLocks
comments: true
---

# Docker 

- Run Docker Container
```
docker run -it \
--name tuya_doorlock \
ghcr.io/sthopeless/tuya_doorlock:latest
```

- Edit the env.py file with your details  
  Exit and Save (CTRL+X and Y)
```
nano /home/tuya_doorlock/env.py
```

- Run python file and test unlocking the DoorLock
```
python3 /home/tuya_doorlock/Zigbee_Doorlock.py
```

- Unlock via MQTT
```
topic: TuyaLock/Doorlock
payload: unlock_door
```  
  
  
Raw files: [{{page.tyfiles}}]({{page.tyfiles}})


