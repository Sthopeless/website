---
layout: post
title: "Open Applications via SSH on another PC"
author: sthope
image: 
categories: [ Ubuntu, SSH, Linux ]
comments: true
---

```
nohup ssh -X [USERNAME@IP] [APPLICATION-NAME]
```

For example:

```
nohup ssh -X sthope@192.168.1.100 gnome-session-properties
```

Or:

```
nohup ssh -X sthope@192.168.1.100 kodi
```
