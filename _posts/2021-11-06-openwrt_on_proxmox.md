---
layout: post
title: "OpenWRT on Proxmox"
description: ""
author: sthope
image: 
categories: [ Proxmox, OpenWRT ]
comments: true
---

Better SSH into Proxmox terminal to copy&paste commands!


```
wget -q https://downloads.openwrt.org/releases/21.02.1/targets/x86/64/openwrt-21.02.1-x86-64-generic-squashfs-combined.img.gz -O openwrt.img.gz; \
gunzip openwrt.img.gz; \
qm importdisk 105 openwrt.img local-lvm
```
