---

layout: post

author: softwareshinobi

title:  "emby media server [docker compose]"

categories: [lifestyle, media server]

tags: [lifestyle,media server,plex,emby,docker,docker compose,linux]

image: https://random.imagecdn.app/820/360

description: "this is a docker compose script to spin up an emby media server."

hidden: false

---

## about this script

this is a docker compose script to spin up an emby media server.

## editor's notes

emby is better than plex.

plex has gotten worse over the years.

needing accounts and registrations and other dumb shit. 

fuck 'em. moved to emby.

## how you can use this

host mp3/mp4/etc style content.

podcasts / music / music / tv / video / porn / etc

i think pictures too.

all that. with emby.

open source. no commercials. share with who you want. listen how you want. free as fuck.

lol this sounds like a commercial for emby. buy now!

## docker-compose.yaml

```yaml
version: "2.3"

services:

  soy-yo-mateo-radio:

    container_name: soy-yo-mateo-radio

    image: emby/embyserver

    volumes:

      - ./container-volume/config:/config # Configuration directory

      - /home/software-shinobi/media:/mnt/share1 # Media directory

    ports:

      - 8096:8096 # HTTP port

      - 8920:8920 # HTTPS port

    restart: always
```

## access the situation

navigate your web browser here:

```
http://localhost:8096

http://10.28.42.28:8096
```
