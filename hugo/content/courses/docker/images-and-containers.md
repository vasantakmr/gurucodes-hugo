---
title: Images and Containers
lastmod: 2019-04-16T09:12:30-08:00
draft: false
description: Some Description
weight: 3
emoji: 🚀
free: true
chapter_start: Learning Core Concepts
---

Accoding to Docker "Containers are a standardized unit of software that allows developers to isolate their app from its environment, solving the “it works on my machine” headache."

We run containers based on the images.

We can run node image by running "docker run node:alpine" which will pull the node:alpine image from the docker hub. But to interact with that image we should type "docker run -it node:apline" running it again will create a new container rather that using the old container.

Where can we get images from:

1. Use an existing, pre-built image eg: via Docker Hub
2. Create our own custom image from Dockerfile

Images are read-only

- docker start <container name>  : to start the container again
- docker run -d —rm <image id> : to start a new container for the mentioned image in detached mode and removed the container when the container is stopped.
- docker images : lists all the available images.
- docker ps -a : lists all the closed and running containers.
- docker image inspect <image id> : does inspection on mentioned image and gives output about that image

Copying files from and to docker containers:  

docker cp localfolder/filename.txt containername:/foldernameincontainer

docker cp containername:/folder/file localfolder

Assigning a name to containers: 

docker run —name appname <imageid> : creates a container for that image id and assigns the container a name.

images and tags:

name:tag is the format for naming images.

docker build -t name:tag .



| Images | Containers |
|--|--|
| Templates/Blueprints for containers. | Running unit of software |
| Contains code + required tools/runtimes. | Multiple containers can be created based on one image |