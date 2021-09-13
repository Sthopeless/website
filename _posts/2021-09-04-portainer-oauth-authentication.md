---
layout: post
title: "Portainer OAuth Authentication"
description: "Login into Portainer using your Github account or even better.. your private Gitea account (with 2FA)"
author: sthope
image: 
categories: [ Docker, Portainer, OAuth ]
comments: true
pic01: "/assets/images/portainer_oauth/1.png"
pic02: "/assets/images/portainer_oauth/2.png"
pic03: "/assets/images/portainer_oauth/3.png"
pic04: "/assets/images/portainer_oauth/4.png"
pic05: "/assets/images/portainer_oauth/5.png"
pic06: "/assets/images/portainer_oauth/6.png"
pic07: "/assets/images/portainer_oauth/7.png"
pic08: "/assets/images/portainer_oauth/8.png"
pic09: "/assets/images/portainer_oauth/9.png"
pic10: "/assets/images/portainer_oauth/10.png"
---


# Github
Login into Github and go to https://github.com/settings/profile on the right side menu near the end enter `Developer settings` and select `OAuth Apps` 
<img src="{{page.pic02}}"/>
<img src="{{page.pic03}}"/>
<br>
<br>
Create your app details
<img src="{{page.pic04}}"/>
`Application name`: Whatever you wanna call it  
`Homepage URL`: eg: http://IP:9000  
`Application description`: can be empty  
`Authorization callback URL`: eg: http://IP:9000  
<br>
<br>
After Github creates the application click on `Generate a new client secret` and copy `Client ID` and the `Secret` it created.
<img src="{{page.pic05}}"/>
<br>
This is it Github Part is finish!
<br>

# Portainer

Open Portainer UI and go to `Settings` on the right side menu then click on `Authentication` under it.
<img src="{{page.pic08}}"/>

Now choose this options, you can use other `Session lifetime` if you want
<img src="{{page.pic09}}"/>
`Automatic user provisioning`: If set ON anyone with Github account will be able to login and Portainer will automaticily create the user without authorizations, better leave it off and handle the users creation/allowance to you.

### OAuth Configuration

<img src="{{page.pic10}}"/>

| :-------------------- | :------------------------------------------ |
| **Client ID**         | ClientID you copied from Github             |
| **Client secret**     | Secret you copied from Github               |
| **Authorization URL** | https://github.com/login/oauth/authozize    |
| **Access token URL**  | https://github.com/login/oauth/access_token |
| **Resource URL**      | https://api.github.com/user                 |
| **Redirect URL**      | your Portainer URL eg: http://IP:9000       |
| **Logout URL**        | *leave empty*                               |
| **User identifier**   | login                                       |
| **Scopes**            | id,email,name                               |

Remember Gitea Username and Portainer Username need to math otherwise create a new username in Portainer with same name or enable `Automatic user provisioning` and then after login disable it again

<br>
<br>  

# Gitea

For Gitea instead of Github, enter your user `Settings` and go to `Applications` and create a new one.

<img src="{{page.pic06}}"/>
`Redirect URL`= use your Portainer URL, eg: http://IP:9000

<br> 

After that is created, Gitea will give you the ClientID and Secret you should save to use with Portainer.
<img src="{{page.pic07}}"/>

Now for Gitea the configs are a little different, follow:

| :-------------------- | :---------------------------------------- |
| **Client ID**         | ClientID you copied from Gitea            |
| **Client secret**     | Secret you copied from Gitea              |
| **Authorization URL** | http://GITEA_URL/login/oauth/authorize    |
| **Access token URL**  | http://GITEA_URL/login/oauth/access_token |
| **Resource URL**      | http://GITEA_URL/login/oauth/userinfo     |
| **Redirect URL**      | your Portainer URL eg: http://IP:9000     |
| **Logout URL**        | *leave empty*                             |
| **User identifier**   | preferred_username                        |
| **Scopes**            | *leave empty*                             |

Should now be configured and you should be able to login using your Gitea Account

Remember Gitea Username and Portainer Username need to math otherwise create a new username in Portainer with same name or enable `Automatic user provisioning` and then after login disable it again