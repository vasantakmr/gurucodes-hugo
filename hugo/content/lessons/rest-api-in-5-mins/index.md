---
title: Learn REST API in 5 mins
lastmod: 2020-08-24T08:08:56-07:00
publishdate: 2020-08-24T08:08:56-07:00
author: Vasanta Kumar
draft: false
description: Learn the fundamentals of REST API by containerizing a Node.js app
tags: 
    - restapi
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

Representational state transfer or REST is an architectural style or you can say a set of rules which developers follow to create interactive applications.

One of the rule states that when a client requests data to the server to perform some operations then the server in return responds with the requested data, or performs requested operations on the data. 

Technically client should be able to get a resource/information when it sends a request to a URL or more precisely URI(uniform resource identifier).

URIs are organized in such a way that, the first part indicates the root endpoint, the remaining part indicates the path to that resource. Each of these URIs/URLs can be called as **endpoints**. 

In simple words you can say **Rest API allows programs to talk to each other over HTTP**.

Now the question comes what is a request?

**Request** is made of 4 things, which are:
1. Endpoint : Endpoint is the total path to the resource.
2. Method:  We know that REST is used to perform operations on data. 

    These operations are CRUD operations

    i.e. create update, read and delete.

    But how does server know what operations to perform for any particular request. So for that we need to sent the operation in the request.

    In Rest API all these curd operations are performed by using http methods called get put post delete. 

    1. **GET**: Get/read resource from the server.
    2. **POST**: Create a new resource on the server.
    3. **PATCH** or **PUT**: Update existing resource on the server.
    4. **DELETE**: Delete existing resource from the server.

    Here are the complete list of http methods.

3. Headers: It contains some additional information that can be sent as part of request. 
    Some of the commonly used headers are: 
    - Accept: It specifies the content types that are valid in the response message
    - Content-Type: It indicates the content type that is used in the body of the request.
        - Example Content Types:
            a. application/xml
            b. application/json
    - user-agent: Contains details about the client browser or client application.
4. data/body : Its the data you want to send to the server.

After sending a request to the server we get a response.

The **response** contains: 

1. Status Code: Status code tell us how things went when we made a request. 
    - If status code is in 200's it means the request is succeeded.
    - 300's means the request is redirected to other URL.
    - 400's it means the request is failed from client side.
    - 500's means there is a failure from server side.
2. Server: It contains the name of the server. Like nginx, netlify, cloudflare, etc
3. Body: It contains the data that client has requested for.
4. and many other headers.

Some other constraints of REST are:

- REST is stateless, i.e. no data about the client request is stored with the server.
- REST works on client-server architecture.
- It provides cacheability.

Lets understand it with an example. For demonstration I'll use a tool called Postman. **Postman** is a free tool to inspect or test Rest APIs. 

In recent years APIs like GRAPHQL, gRPC, are coming up with new features, but REST API has its own legacy and its ease of use makes it the default choice among many professionals out there.

So this is REST API in 5 mins. This is my first article. If you love my work, show me some support by sharing this article with your friends and let them know that "REST API" is not as hard as it sounds.

## Code Breakdown

### Dockerfile

A Dockerfile is like DNA for building a Docker Image. 

{{< file "docker" "Dockerfile" >}}
```docker
FROM node:12

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

ENV PORT=8080

EXPOSE 8080

CMD [ "npm", "start" ]
```

### Dockerignore

A Dockerignore file is required so we don't add the node_modules folder to the image.

{{< file "docker" ".dockerignore" >}}
```docker
node_modules
```


### Node.js App

This is the code we went to run as the container's process.

{{< file "js" "src/index.js" >}}
```javascript
const app = require('express')();

app.get('/', (req, res ) => 
    res.json({ message: 'Docker is easy 🐳' }) 
);

const port = process.env.PORT || 8080;

app.listen(port, () => console.log(`app listening on http://localhost:${port}`) );
```

## Commands

### Build the Image

{{< file "terminal" "command line" >}}
```bash
docker build -t gurucodes/demoapp:1.0 .
```

### Run the Container

This maps the local port 5000 to the docker port 8080. You should be able to view the app on your local system at `https://localhost:5000`. You can choose any port you want. 

{{< file "terminal" "command line" >}}
```bash
docker run -p 5000:8080 <image-id>
```


## Docker Compose

[Docker Compose](https://docs.docker.com/compose/) makes it easy to manage multiple containers and volumes. 

{{< file "yaml" "docker-compose.yml" >}}
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "8080:8080"
  db:
    image: "mysql"
    environment: 
      MYSQL_ROOT_PASSWORD: password
    volumes:
      - db-data:/foo

volumes:
  db-data:
```

### Run multiple Containers

{{< file "terminal" "command line" >}}
```bash
docker-compose up
```

## Docker in 100s

<!-- {{< youtube Gjnup-PuquQ >}} -->

