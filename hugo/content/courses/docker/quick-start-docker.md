---
title: "Quick Start: Docker"
lastmod: 2019-04-16T09:12:30-08:00
draft: false
description: Start your docker container in 10 mins. 
weight: 4
emoji: 🧟
free: true
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

### Installation

Install Docker Desktop from https://www.docker.com/products/docker-desktop.

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
