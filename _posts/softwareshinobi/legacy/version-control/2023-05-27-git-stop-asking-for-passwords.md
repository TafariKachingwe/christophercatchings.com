---

layout: post

author: softwareshinobi

title:  "Git Won't Stop Asking For My Passwords"

categories: [git]

tags: [git,gitea]

image: https://random.imagecdn.app/820/360

description: "Git won't stop being annoying and asking for passwords. this article teaches you how to fix that"

hidden: false

---

Git won't stop being annoying and asking for passwords. this article teaches you how to fix that.

## the issue

Git won't stop being annoying and asking for passwords everytime you do something.

## 1. run this

```bash
git config --global credential.helper store
```

## 2. run this

run a git command that hits the server. 

```bash
git pull
```

you will be asked for your username and password again.

## 3. run this

now let's run git pull again. this time it shouldn't ask anything.

```bash
git pull
```

## solution #2

temporarily store credentials but dont save.

caching.

```bash
git config --global credential.helper cache
```

```bash
git config --global credential.helper 'cache --timeout=600' // 10 minutes
```
