---
layout: post
title: "Custom cmds in Ubuntu"
description: "Create custom commands in Ubuntu (and other Linux distros)."
author: sthope
image: "bash-logo.png"
categories: [ Ubuntu, Linux ]
distro_tested: "Ubuntu 20.04"
comments: true
---


<strong>⚠️⚠️⚠️</strong> This was done using {{page.distro_tested}} but it should work on most Linux distros the same way. 


<h2 id="part1">Create Folders</h2>
On the terminal create folder to save your customs scripts eg:

```
mkdir -p ~/bin
```

<h2 id="part2">Create Scripts</h2>
Inside the new folder created create a new file,eg:  
`nano ~/bin/y2upgrade`

<h2 id="part3">Edit the Scripts</h2>
Edit the file with your commands and save, eg:
  
```
#!/bin/bash

sudo apt-get update
sudo apt-get upgrade -y
```

<h2 id="part4">Set Access Permissions</h2>
Use chmod to set files permissions. (should ask twice for sudo password)

```sudo chmod +x ~/bin/*;su -l $USER```

<h2 id="part5">Testing</h2>
Now you should be able to send your command from the terminal, the file name is the command name for example now when entering: `y2upgrade` it should first do `sudo apt-get update` and then `sudo apt-get upgrade -y`.<br>
<br>
`-y` simply means it will not ask you Y/n if you want to accept installing the upgrades in case there is any.

<h2 id="part5">Extra</h2>
SSH without asking for password.<br>
Create file named `sshnopwd` and paste the [contents of this file](https://git.sthope.dev/sthope/sthope-examples/src/branch/master/custom-cmds-in-ubuntu/bin_examples/sshnopwd)<br>

now instead of using `ssh username@ip` and then entering password, simply run `sshnopwd password username@ip` and it will automatically login.<br>

Small collection with more examples can be found [here](https://git.sthope.dev/sthope/sthope-examples/src/branch/master/custom-cmds-in-ubuntu/bin_examples)