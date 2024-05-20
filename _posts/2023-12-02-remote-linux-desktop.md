---

layout: post

author: softwareshinobi

title: "spinning up a pristine linux desktop environment in the cloud"

categories: [linux,docker]

tags: [hacker,security,desktop,vnc,rdp,docker,docker,docker compose,linux,cloud]

image: https://random.imagecdn.app/820/360

description: "docker compose script to spin up a remote linux desktop environment with a desktop and vnc server baked in."

hidden: false

---

## about this script

this is a docker compose script to spin up a remote linux desktop environment with a desktop and vnc server baked in.

## docker-compose.yaml

```yaml
version: "3"

services:

    software-shinobi-desktop:

        container_name: software-shinobi-desktop

        image: dorowu/ubuntu-desktop-lxde-vnc

        restart: always

        environment:

            - USER_UID=1000

            - USER_GID=1000

        volumes:

            - /dev/shm:/dev/shm

            - ./container-desktop/:/root/

            - /etc/timezone:/etc/timezone:ro

            - /etc/localtime:/etc/localtime:ro

        ports:

            - 8888:80
```

## run the docker compose script

```bash
docker-compose down

docker-compose up
```

## access the desktop environment

navigate your browser here:

localhost example

```
http://localhost:8888
```

remote server example

```
http://28.28.28.28:8888
```
