---
layout: post
title: "Dockerfile & Github"
description: "create a simple docker container and upload it to Github"
author: sthope
image: "dockergithub.png"
categories: [ Docker, Github ]
github_create_token: 'https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-token'
github_auth: 'https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry#authenticating-to-the-container-registry'
docker_template_repo: 'https://github.com/Sthopeless/dckrtmplt'
comments: true
---

![dockergithub](assets/images/dockergithub.png)

## Setup and configure Github Token
1. [Create Github Token]({{page.github_create_token}}) and save the token.
2. [Authenticate]({{page.github_auth}}) with:  
  (replace 'YOUR_TOKEN' with token from last step)
```
export CR_PAT=YOUR_TOKEN
```

3. Last sign in with:  
  (replace 'USERNAME' with your Github Username)
```
echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin
```

## Setup container files

1. [Download this repository]({{page.docker_template_repo}})
2. Open terminal, go to the repo location (eg: ~/Documents/dckrtmplt) and do:
```
docker build -t dckrtmplt . ; \
docker tag dckrtmplt ghcr.io/sthopeless/dckrtmplt:latest ; \
docker push ghcr.io/sthopeless/dckrtmplt:latest
```

3. Your new Package should be visible at:<br>
  [https://github.com/Sthopeless?tab=packages](https://github.com/Sthopeless?tab=packages)<br>
  (replace 'Sthopeless' with your Github Username)
4. You can test running:
```
docker run -it --rm ghcr.io/sthopeless/dckrtmplt:latest
```
5. Set package visibility from Private to Visible, follow pictures:

1.<br>
<img src="/assets/images/githubdocker/1.png" width="80%" height="80%"><br>
2.<br>
<img src="/assets/images/githubdocker/2.png" width="80%" height="80%"><br>
3.<br>
<img src="/assets/images/githubdocker/3.png" width="80%" height="80%"><br>
