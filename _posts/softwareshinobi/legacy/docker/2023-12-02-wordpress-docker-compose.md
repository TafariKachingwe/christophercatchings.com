---

layout: post

author: softwareshinobi

title:  "spinning up a wordpress server using docker compose"

categories: [wordpress,docker]

tags: [wordpress,docker,docker,docker compose,linux]

image: https://random.imagecdn.app/820/360

description: "this is a docker compose script to spin up a wordpress server."

hidden: false

---

## about this script

this is a docker compose script to spin up an wordpress server.

## how you can use this

run a blog

run a website

run an online store

run a portfolio

and more

## docker-compose.yaml

```yaml
version: "3"

services:

  software-developer-things-database:

    image: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: aggiepride
      MYSQL_DATABASE: sdt_shop
      MYSQL_USER: sdt_shop
      MYSQL_PASSWORD: sdt_shop
    volumes:
      - ./volume-database:/var/lib/mysql

  software-developer-things-shop:
    depends_on:
      - software-developer-things-database
    image: wordpress:latest
    restart: always
    ports:
      - "777:80"
    environment:
      WORDPRESS_DB_HOST: software-developer-things-database:3306
      WORDPRESS_DB_USER: sdt_shop
      WORDPRESS_DB_PASSWORD: sdt_shop
      WORDPRESS_DB_NAME: sdt_shop
    volumes:
      ["./volume-wordpress:/var/www/html"]
```

## access the situation

navigate your web browser here:

```
http://localhost:777

http://10.28.42.28:777
```
