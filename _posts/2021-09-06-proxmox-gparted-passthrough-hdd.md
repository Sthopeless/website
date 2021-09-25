---
layout: post
title: "Proxmox Harddrive PassThrough"
description: ""
author: sthope
image: 
categories: [ Proxmox, GParted ]
comments: true
pic01: "/assets/images/proxmox_gparted1.png"
pic02: "/assets/images/proxmox_gparted2.png"
---

On Proxmox create a VM using [GParted](https://gparted.org/download.php) iso
And go to the Terminal of Proxmox and enter:
```
clear;ls -l /dev/disk/by-id/
```
{{page.pic01}}

Then copy the correct name of your Harddrive and on Proxmox terminal add it to gparted VM with:
```
qm set 101 -scsi2 /dev/disk/by-id/ata-FORESEE_128GB_SSD_J30992J013821
```
{{page.pic02}}
