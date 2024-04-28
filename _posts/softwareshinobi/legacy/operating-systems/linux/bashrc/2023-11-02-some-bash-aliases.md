---

layout: post

author: softwareshinobi

title:  "a bunch of bash aliases you can use"

categories: [linux,bashrc]

tags: [linux,bashrc]

image: https://random.imagecdn.app/820/360

description: "a bunch of bash aliases you can use"

hidden: false

---

## introduction

this is a just a collection of aliases you can use on your linux servers and linux productivity machines.

## what these bash aliases do

you are basically creating custom terminal commands that do whatever you want.

## how to use these bash aliases

just copy and paste the aliases into your `.bashrc` file. close any existing terminal windows.

## what happens after you set these up

you will use the linux terminal like normal BUT now you can use the bash aliases like terminal commands.


## editing the `.bashrc` file

you can find this file here:

```sh
nano ~/.bashrc
```

## directory traversal

move up and down directory trees like a boss.

```sh
alias cd..='cd ..'
alias ..='cd ..'
alias ...='cd ../../../'
alias ....='cd ../../../../'
alias .....='cd ../../../../'
alias .4='cd ../../../../'
alias .5='cd ../../../../..'
```

## system cpu usage

what process is fucking my processors?

```sh
alias @cpu-info='lscpu'
alias @cpu-usage-all='ps auxf | sort -nr -k 3'
alias @cpu-usage-top='ps auxf | sort -nr -k 3 | head -3'
```

## system memory usage

what process is destroying my ram?

```sh
alias @memory-info='free -m -l -t'
alias @memory-usage-all='ps auxf | sort -nr -k 4 | head -10'
alias @memory-usage-top='ps auxf | sort -nr -k 4 | head -3'
```

## more bash aliases on the internet

other people's shit.

* https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html
* https://opensource.com/article/19/7/bash-aliases
* https://davidjguru.github.io/blog/linux-70-commands-aliases-for-everyday-life
* https://davidjguru.github.io/blog/linux-200-commands-for-everyday-life
* https://davidjguru.github.io/blog/linux-random-commands-for-your-daily-life
* https://aruva.medium.com/100-bash-aliases-for-supersonic-productivity-d54a796422d9

## namaste.
