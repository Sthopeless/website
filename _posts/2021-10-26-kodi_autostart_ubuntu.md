---
layout: post
title: "Autostart Kodi on Ubuntu"
description: ""
author: sthope
image: 
categories: [ Kodi, Ubuntu ]
comments: true
---

SSH into your Ubuntu or open the terminal and type:
mkdir -p ~/.config/autostart;nano ~/.config/autostart/kodi.desktop

And paste:
```
[Desktop Entry]
Type=Application
Exec=kodi -d 5 --standalone -fs
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_En]=Kodi
Name=Kodi
Comment[en_En]=
Comment=
```

Reboot machine and Kodi should autostart.
Works best on Ubuntu installations with auto-login enabled.
