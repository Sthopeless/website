---
layout: post
title: "Samba Docker Container"
description: "Installing and configuring Samba using Docker and Portainer Stacks"
author: sthope
image: samba-logo.png
comments: true
categories: [ Docker, Samba, Portainer, Stacks ]
samba_repo: "https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/samba"
env_file: "https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/samba/config.env"
dockercompose: "https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master/samba/samba.yml"
samba_portainer_example: "/assets/images/samba_example.png"
repository_url: "https://git.sthope.dev/sthope/sthope-examples/src/branch/master/docker_portainer_stacks/src/branch/master"
compose_path: "samba/samba.yml"

---

### 1. Terminal via cmdline

Open terminal, copy, adapt and send:
```
docker run -d \
-p 139:139 \
-p 445:445 \
-e TZ=Europe/Lisbon \
-v /docker:/share \
elswork/samba:latest \
-u "1000:1000:USERNAME:USERNAME:PASSWORD" \
-s "SmbShare:/share:rw:USERNAME"
```
<br>
<br>
### 2. Environments File

On the PC create environments text file named e.g. `configs.env` or download the file from [here]({{page.env_file}})
```
USERNAME=JApoOgeY1PF7qqylo4
PASSWORD=uJ6CYqSp266IiijD7K

folder_to_share=/docker/

PUID=1000
PGID=1000

TZ=Europe/Lisbon

Reset_Mode=unless-stopped
tag_samba=latest
watchtower_autoupdate=false
```
<br>
Adapt to your needs.<br>
`folder_to_share` is the folder you want to share over smb.<br>
`USERNAME` & `PASSWORD` are the login details you will be using.<br>
`PUID` & `PGID` are you `user id` and your `group id`. default generally is `1000`.<br>
`TZ` is your timezone.<br>

If you are not sure what to do about `Reset_Mode` & `tag_samba` & `watchtower_autoupdate` leave them as they are.
<br>
<br>
### 3. Deploy using a Git repository

Choose `Repository` option as building method.

**Reposity URL:**
```
{{page.repository_url}}
```
<br>
**Compose path:**
```
{{page.compose_path}}
```
<br>
<br>
Example:
![]({{page.samba_portainer_example}})
<br>
<br>
### 4. Testing
<br>
If you are using Windows 🙄 the folder should now be available opening File Explorer and navigating to: `\\samba_IP`

On Linux distros should be available navigating to: `smb://samba_ip`