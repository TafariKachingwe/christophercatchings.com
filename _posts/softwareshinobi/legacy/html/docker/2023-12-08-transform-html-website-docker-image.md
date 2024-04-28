---

layout: post

author: softwareshinobi

title:  "Transform Your HTML Source Code Into A Docker Image [2023]"

categories: [html,docker]

image: assets/images/softwareshinobi/html/docker/transform-html-website-docker-image.png

description: "In this docker guide you'll learn how to transform your HTML source code into a Docker image using a Dockerfile and Docker Compose."

tags: [sticky,featured,guide,html,how-to,docker,docker image,docker compose,]

hidden: false

---

Learn how to turn your HTML source code into a Docker image using a linux server, a Dockerfile and Docker Compose.

## introduction

In this docker guide you'll learn how to transform your HTML source code into a Docker image using a Linux Server, a Dockerfile and Docker Compose.

## why you'd wanna do this

at some point you'll have to deploy your html app to a big boy server. the big boy server should be using a container situation like docker.

* containers provide pristine execution environments
* containers eliminate differences in development and production environments
* containers are portable across server operating systems and architectures
* containers give you the flexibility of virtual machines without the overhead

## what you'll need

* Ubuntu server with sudo/root permissions

## what you'll do

1. clone html project from github [optional]
1. update operating system packages
1. install docker compose
1. create a dockerfile
1. create a docker compose file
1. build docker image using docker compose
1. run and verify HTML web site docker image

## clone a sample HTML project from github [optional]

if you don't have html code that you want to use, then use mine.

use the command below to clone a trivial html website from my GitHub account.

this trivial html website is just a dashboard template from the internet. it doesn't do anything special, but it's pretty.

```bash
git clone https://github.com/software-shinobi/trivial-html-web-site.git
```

change directories into the github clone repository.

```bash
cd trivial-html-web-site
```

now you are ready to follow along with the rest of the article.

## update operating system packages

let's update the Aptitude package lists before we install the Docker Compose software and dependencies.

```bash
sudo apt-get update
```

the OS will update packages references.

```
[sudo] password for software-shinobi: 
Hit:1 http://co.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://co.archive.ubuntu.com/ubuntu jammy-updates InRelease                               
Hit:3 http://co.archive.ubuntu.com/ubuntu jammy-backports InRelease                             
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease                                
Hit:5 https://brave-browser-apt-release.s3.brave.com stable InRelease                           
Hit:6 https://dl.google.com/linux/chrome/deb stable InRelease                                   
Loading package lists... 98%
```

## install docker compose

docker compose is a docker container orchestration situation. we'll use docker-compose to define and run container configurations.

the command below will install docker compose on your ubuntu linux server.

```bash
sudo apt-get install -y docker-compose
```

the OS will fetch and install docker compose and the dependencies.

## create a dockerfile

To create a Docker image we have to create a `Dockerfile`.

A `Dockerfile` contains the instructions to be executed to build a custom docker image.

You can name your `Dockerfile` simply: "Dockerfile"

```bash
touch Dockerfile
```

update the `Dockerfile` contents as follows.

### file contents: Dockerfile

```
##
## Dockerfile to transform HTML web site into Docker Image
##

FROM httpd

MAINTAINER Software Shinobi "the.software.shinobi@gmail.com"

USER root

## set build environment variables

ENV webServerFileRoot /usr/local/apache2/htdocs/

##

RUN rm -rf $webServerFileRoot

COPY ./ $webServerFileRoot

RUN ls -lha $webServerFileRoot

## Expose ports

EXPOSE 80

```

## create a docker compose file

Docker compose can build the docker image for us, we just need to create the configuration in a `docker compose yaml file`.

A `docker-compose.yaml` contains instructions to be executed to build a custom docker image.

the following docker compose configuration will bundle the HTML web site code using the Dockerfile that we just created.

You can name your `docker-compose.yaml`: "docker-compose.yaml"

```bash
touch docker-compose.yaml
```

update the `docker-compose.yaml` contents as follows.

### file contents: docker-compose.yaml

```
version: '3.8'

services:

    trivial-html-web-site:
        
        build: 

            context: .

            dockerfile: Dockerfile

        container_name: trivial-html-web-site

        image: softwareshinobi/trivial-html-web-site

        ports:

            - "8888:80"

```

note: while the `container_name` and `image` appear to match the github repository URLs, you can choose ANY names you want in this specific docker-compose file.

## build docker image using docker compose

```bash
docker-compose build
```

This command will build the docker image using the dockerfile in the current directory. When the container is built, the output will look like this:

```
Building trivial-html-web-site
Sending build context to Docker daemon  25.13MB
Step 1/8 : FROM httpd
latest: Pulling from library/httpd
Digest: sha256:04551bc91cc03314eaab20d23609339aebe2ae694fc2e337d0afad429ec22c5a
Status: Downloaded newer image for httpd:latest
 ---> a6ca7b52a415
Step 2/8 : MAINTAINER Software Shinobi "the.software.shinobi@gmail.com"
 ---> Using cache
 ---> 9836d0aaaa14
Step 3/8 : USER root
 ---> Using cache
 ---> 5648019457ba
Step 4/8 : ENV webServerFileRoot /usr/local/apache2/htdocs/
 ---> Using cache
 ---> 209a5fb41f71
Step 5/8 : RUN rm -rf $webServerFileRoot
 ---> Using cache
 ---> 4239b2919911
Step 6/8 : COPY ./ $webServerFileRoot
 ---> fcd3caccb234
Step 7/8 : RUN ls -lha $webServerFileRoot
 ---> Running in 26b5403ead1d
total 644K
drwxr-xr-x 6 root root 4.0K Dec  8 20:07 .
drwxr-xr-x 1 root root 4.0K Dec  8 20:06 ..
drwxrwxr-x 8 root root 4.0K Dec  8 19:56 .git
-rw-rw-r-- 1 root root  359 Dec  8 19:57 Dockerfile
-rw-rw-r-- 1 root root 1.8K Dec  8 19:56 README.md
drwxrwxr-x 5 root root 4.0K Dec  8 19:56 assets
-rw-rw-r-- 1 root root  58K Dec  8 19:56 dashboard-finance.html
-rw-rw-r-- 1 root root  77K Dec  8 19:56 dashboard-influencer.html
-rw-rw-r-- 1 root root  63K Dec  8 19:56 dashboard-sales.html
-rw-rw-r-- 1 root root  281 Dec  8 20:06 docker-compose.yaml
drwxrwxr-x 5 root root 4.0K Dec  8 19:56 documentation
-rw-rw-r-- 1 root root  52K Dec  8 19:56 ecommerce-product-checkout.html
-rw-rw-r-- 1 root root  57K Dec  8 19:56 ecommerce-product-single.html
-rw-rw-r-- 1 root root  65K Dec  8 19:56 ecommerce-product.html
-rw-rw-r-- 1 root root  75K Dec  8 19:56 index.html
-rw-rw-r-- 1 root root  72K Dec  8 19:56 influencer-finder.html
-rw-rw-r-- 1 root root  74K Dec  8 19:56 influencer-profile.html
drwxrwxr-x 2 root root 4.0K Dec  8 19:56 pages
Removing intermediate container 26b5403ead1d
 ---> d35e91eae83a
Step 8/8 : EXPOSE 80
 ---> Running in bbd2327ca37f
Removing intermediate container bbd2327ca37f
 ---> 84835f6c10ff
Successfully built 84835f6c10ff
Successfully tagged softwareshinobi/trivial-html-web-site:latest
```

## run and verify HTML web site docker image

So our custom docker image has been built containing the static HTML code. Let's run the docker image and create a new docker container.

```bash
docker-compose up
```

This command will start a docker container using the configuration from the `docker-compose.yaml` file. You'll see output like the following:

```
Starting trivial-html-web-site ... done
Attaching to trivial-html-web-site
trivial-html-web-site    | AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message
trivial-html-web-site    | AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message
trivial-html-web-site    | [Fri Dec 08 20:20:09.930361 2023] [mpm_event:notice] [pid 1:tid 139753100785536] AH00489: Apache/2.4.58 (Unix) configured -- resuming normal operations
trivial-html-web-site    | [Fri Dec 08 20:20:09.931257 2023] [core:notice] [pid 1:tid 139753100785536] AH00094: Command line: 'httpd -D FOREGROUND'
```

The HTML web site is up. now let's verify using our browser.

Open up your favorite internet browser and navigate to the URL below if running on local:

```
http://localhost:8888/
```

Open up your favorite internet browser and navigate to the URL below if running on a remote server:

```
http://24.13.21.52:8888/
```

You should see your html app under this address. If you do... then you are all done!
