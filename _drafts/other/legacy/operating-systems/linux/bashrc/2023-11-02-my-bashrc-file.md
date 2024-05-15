---

layout: post

author: softwareshinobi

title:  "Senior Developer REVEALS personal BASHRC file"

categories: [linux,bashrc]

tags: [linux,bashrc]

image: https://random.imagecdn.app/820/360

description: "Senior Developer REVEALS personal BASHRC file"

hidden: false

---

## introduction

this is my bashrc file situation on my home linux workstation, pandora.

## how it works

1. the primary bashrc file `~/.bashrc` is modified to run the secondary bashrc.

1. the secondary bashrc file `~/.$USER.bashrc` contains the extended configurations.

## add this to your bashrc file [~/.bashrc] first

open up the bashrc file.

```bash
nano ~/.bashrc
```

ADD the following text on a blank line to your bashrc file.

```
source ~/.$USER.bashrc
```

`note`: existing content in the bashrc file can remain unchanged

## add in the custom bashrc stuff [~/.$USER.bashrc]

```bash
#!/bin/bash

## aliases for accessing cloud desktops

alias dione="ssh root@167.71.184.7"

alias ip="dig +short myip.opendns.com @resolver1.opendns.com"

alias blog="ssh software-shinobi@valorantdigital.online"

##
## docker aliases
##

alias d.stop="docker stop $(docker ps -a -q)"

alias d.prune="docker system prune -a -f"

##
## uncategorized
##

alias r="reset;clear;"

alias push="reset;clear;git add .;git commit -m 'automated terminal push';git push origin;"

alias pushe="reset;clear;git add .;git commit -m 'automated terminal push';git push origin;exit;"

alias mount-silver="reset;clear;sudo mount /dev/sdb1/ /media/silver-hard-drive/partition-one/;sudo mount /dev/sdb2/ /media/silver-hard-drive/partition-two/"

##

alias shinobiNET='ssh software-shinobi@shinobinet.online'

##

alias tunnel="sudo ssh -L 8080:127.0.0.1:80 valorant-digital@shinobinet.online"

alias vpn="sudo killall openvpn;sudo openvpn ~/.shinobiNET-openvpn-config.ovpn"

#alias @vpn="vpn"

```

## namaste.
