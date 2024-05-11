---

layout: post

author: softwareshinobi

title:  "setting up a postgres database + pgadmin4 using docker compose [ubuntu linux]"

categories: [postgres,docker]

tags: [docker, docker compose,relational database,postgres,pgadmin]

image: https://random.imagecdn.app/820/360

description: "this is a docker compose configuration to spin up a postgres database plus the administration website."

hidden: false

---

## about this script

this is a docker compose configuration to spin up a postgres database plus the administration website.

## docker-compose.yaml

```yaml
version: "3"

services:

    lorem-ipsum-postgres:

        container_name: lorem-ipsum-postgres
        
        image: postgres:14.1-alpine

        restart: always

        environment:

            - POSTGRES_USER=loremipsum

            - POSTGRES_PASSWORD=loremipsum

        ports:

            - "5432:5432"

        volumes: 

            - ./container-volume/postgres/:/var/lib/postgresql/data

    lorem-ipsum-pgadmin4:

        container_name: lorem-ipsum-pgadmin4

        image: dpage/pgadmin4
        
        restart: always

        ports:
        
            - "5480:80"
            
        environment:
        
            PGADMIN_DEFAULT_EMAIL: lorem@loremipsum.com
            
            PGADMIN_DEFAULT_PASSWORD: lorem!!ipsum

        volumes:
        
            - ./container-volume/pgadmin4/:/var/lib/pgadmin

```
