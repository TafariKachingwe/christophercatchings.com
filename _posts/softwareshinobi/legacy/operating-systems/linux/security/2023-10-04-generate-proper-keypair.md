---

layout: post

author: softwareshinobi

title:  "generating proper RSA ssh keys [linux security]"

categories: [linux,security]

tags: [linux,security,public key, private key, key infrastructure,ssh-keygen]

image: https://random.imagecdn.app/820/360?kk

description: "ssh-keygen -m PEM -t rsa -b 4096"

hidden: false

---

## introduction

use this command to generate a private and public key for a linux users.

## why this matters

the key created by the default `ssh-keygen` are bad and should be avoided.

if you do not generate an RSA type key, when you set up linux key authentication you can get strange security errors.

This was happening alot with my Digital Ocean servers OOTB.

The fix is to generate RSA keys, NOT OpenSSH keys.

## disclaimer

don't listen to me. this is just how i manage my servers.

do whatever you want. or don't. whatever.

## how to do it

run this as the user who needs a new key situation.

```bash
ssh-keygen -m PEM -t rsa -b 4096
```

## how you know you did it right.

run this to print your private key.

```bash
cat ~/.ssh/id_rsa
```

look for the following mentioning `RSA`.

```
gAxZllpH7gnPDp/Qx7sLLd0j5ByEWWYx3CdturHWOdrhvE//bI7xqUTYG5rGFbC9
BRKyN4QO4RCvGt7EHbfdmWd0JtSI/Qo09aI7Hen+jIrIfLagvJfUzOdvZOpijljU
TKVL1xiYdxw3xa4l+upNdaW8oRoNqgfy8cX2fP0EzyNzJLyADnCAmG+VIGR2LgK1
ZdHeaZjkeuTDmVEnhByE8IJZpvjcc/iVQ+Jl5W6Ur4ljL95DRHG1Kd5f4F53h1nf
tvELJTD/ULf+MOq+hM1C2siAzVRXKl/ORUsOZAiEIbSfrMMDDhnJmpR+KXs=
-----END RSA PRIVATE KEY-----
```

## namaste.
