---

layout: post

author: softwareshinobi

title:  "use this docker compose file to build a docker image"

categories: [postgres,docker]

tags: [docker compose,compose,database,postgres,pgadmin]

image: https://random.imagecdn.app/820/360

description: "use this docker compose file to build a docker image."

hidden: false

---

## about this script

use this docker compose file to build a docker image

## docker-compose.yaml

```yaml
version: '3.8'

services:

    software-shinobi-linux:
        
        build: 

            context: .

            dockerfile: Dockerfile

        container_name: software-shinobi-linux

        hostname: software-shinobi-linux

        image: softwareshinobi/software-shinobi-linux

        domainname: linux.softwareshinobi.online

        ports:

            - "2222:22"
```
