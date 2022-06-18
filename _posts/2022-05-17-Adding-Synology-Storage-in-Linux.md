---
layout: post
title: "Adding Synology Storage in Ubuntu"
author: sthope
image: 
categories: [ Sthope  ]
comments: false
---

1. Update system and install dependencies
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install -y smbclient cifs-utils
```

2. Create Synology credentials file
```
nano /etc/.synology
```

With:
```
username=Synology_USERNAME
password=Synology_PASSWORD
```

3. Mount Storage Automaticly on boot
```
sudo nano /etc/fstab
```

And add at the end of the file:
```
//Synology_IP/storage_name /mnt/synology cifs credentials=/etc/.synology,vers=3.0,uid=1000,gid=1000 0 0
```

Save and run (or reboot)
```
sudo mount -a
```

|                            |                            |
| :------------------------- | :------------------------- |
| //Synology_IP/storage_name | your Synology IP           |
| /storage_name              | your Synology Storage Name |
| /mnt/synology              | where you want it to mount |
| /mnt/synology              | where you want it to mount |
| uid=1000                   | userID check with ID       |
| gid=1000                   | groupID check with ID      |
