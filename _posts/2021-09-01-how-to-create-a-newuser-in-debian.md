---
layout: post
title: "How to create a new User in Debian"
description: ""
author: sthope
image: 
categories: [ Docker, Portainer, Stack, LinuxServer ]
comments: true
pic01: /assets/images/adduser_result.png
---

*Should also work on most Linux distros*

```
adduser sthope
```

It will then ask to assign a password to the new username and some unnecessary questions
![result example]({{page.pic01}})

Make sure `sudo` is installed:
```
apt-get update;apt-get upgrade -y; apt-get install -y sudo
```
It will update, upgrade the system if necessary then install sudo.

You can now give sudo permissions to the new user created:
```
usermod -aG sudo sthope
```

If you have Docker also installed and want to also give permissions to the new created user, use this instead:
```
usermod -aG sudo sthope;usermod -aG docker sthope

```

Finally test the new user, either reboot system or enter:
```
su -l sthope
```

In case Debian is running on Proxmox installed via my scripts LXC will automatically login into root user, to change that edit the file (remember to user sudo is editing with the new created user, not necessary if using the root user)
```
nano /etc/systemd/system/container-getty@1.service.d/override.conf
```

And search for `--autologin root` and replace root with your new username create, e.g. `--autologin sthope`
Save and reboot, system should now automatically login into the new user instead of root
<br>
<br>
<br>
<br>
1-Line command, replace Username and Password with your details and run:
```
bash -c "$(wget -qLO - https://git.sthope.dev/sthope/sthope-examples/src/branch/master/custom-cmds-in-ubuntu/bin_examples/proxmox_addnewuser)" Username Password
```

It will Update & Upgrade system, install sudo, create Username with Password provided and give new created User `sudo` and `docker` permissions.