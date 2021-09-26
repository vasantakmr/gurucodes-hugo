---
title: Docker Basics Tutorial with Node.js
lastmod: 2020-08-24T08:08:56-07:00
publishdate: 2020-08-24T08:08:56-07:00
author: Vasanta Kumar
draft: false
description: Learn the fundamentals of Docker by containerizing a Node.js app
tags: 
    - docker
    - node

# youtube: gAkwW2tuIqE
github: https://github.com/gurucodes-io/docker-nodejs-basic-demo
# disable_toc: true
# disable_qna: true

# courses
# step: 0

# versions:
#    rxdart: 0.20
---

## Create your App

### Node.js App

Create a package.json file in your project folder.

{{< file "js" "package.json" >}}
```json
{
  "name": "dummy",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
    "dependencies": {
    "express": "^4.17.1"
  }
}
```

Lets write a simple rest endpoint in express;

{{< file "js" "index.js" >}}
```javascript
const app = require('express')();

app.get('/', (req, res ) => 
    res.json({ message: 'Docker is awesome 🐳' }) 
);

app.listen(8000, () => console.log(`Listening on 8000`) );
```

### Dockerfile

Create a file named Dockerfile in your project directory and write your configuration.

{{< file "docker" "Dockerfile" >}}
```docker
FROM node:14-alpine

WORKDIR /app

COPY package.json ./

RUN npm install

COPY . .

ENV PORT=8080

EXPOSE 8080

CMD [ "node", "index.js" ]
```
We are using nodejs 14-alpine version. Visit [dockerhub](https://hub.docker.com/_/node) to see all available nodejs versions. 

### .dockerignore

A Dockerignore file prevents files/folders from getting copied to the image. 
We are here ignoring node_modules folder as it will be regenerated in the image.

{{< file "docker" ".dockerignore" >}}
```docker
node_modules
```


## Commands

### Build the Image

Change to project directory in terminal and execute the following command.
This assigns a name to our image as gurucodes/dummy.

{{< file "terminal" "command line" >}}
```bash
docker build -t gurucodes/dummy .
```

### Run the Container

This creates a container based on our image i.e., gurucodes/dummy and maps local port 5000 to docker container port 8000. Your app can be accessed in your local machine at `http://localhost:5000`.

{{< file "terminal" "command line" >}}
```bash
docker run -p 5000:8000 gurucodes/dummy
```

## Summary

### Commands Cheatsheet

Builds the image and assigns it a name and tag.

{{< file "terminal" "command line" >}}
```bash
docker build -t imageName:tag .
```

Creates a container for the mentioned image_id/name and maps docker machine port to local machine port.

{{< file "terminal" "command line" >}}
```bash
docker run -p localMachinePORT:dockerContainerPORT <image-id>
```
