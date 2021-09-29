---
title: "Why Docker Exists?"
lastmod: 2019-04-16T09:12:30-08:00
draft: false
description: Problems addressed by Docker.
weight: 1
emoji: 📜
chapter_start: Dive Into Docker
free: true
---

Before diving into the course, I want you to understand Docker's impact on our lives. So we'll discuss "why it exists" before "what it is" because it helps us realize the effect of a tool on our lives.


## Problems Faced By Developers

What exact problem is Docker trying to solve? 🧐 

For developers, installing software or running a codebase in a new machine requires a lot of effort and troubleshooting. Many complex setups take even days, if not weeks, just to set up the codebase. Let's see a typical workflow of setting up a codebase in a new machine.

{{< figure src="/courses/docker/img/why-docker.png" caption="Typical Workflow of Code Setup" >}}


Here if you see developers might have issues while installing software or setting up the codebase. For example, there might be some version mismatches, or some dependency might not be present in the new machine. So, troubleshooting these issues takes a lot of effort and makes the whole process less productive for developers. 

Other common problems faced by developers are:
- Version mismatch in different machines or change in the development environment. Even a change in operating systems or minor tweaks can cause a variance in the behavior of that development environment. Example: I developed a NodeJS app in my local machine with NodeJS 14 installed, and the production environment has NodeJS 12 installed. This version mismatch can cause problems. With every new version, the software brings some breaking changes. So, code made for a particular version might not work if the developer installed/has a different version of that software in the machine.
- Let's assume that developer had no problem setting up the code, and it runs perfectly. Even in that case, while testing the developed software, there might be issues or changes in behavior because they are being run in different machines. So testers will have a hard time testing it as they don't have the same environment as the developer. 
- Clashing versions/tools between different projects can also be a problem. For example, a developer might be working on two different projects, and one of these projects requires python 2.7, and another requires 3.5. Here, developers will have to install the respective versions every time they switch between the projects, which is not easy.

### What we software developers want?
- We want to have a common environment for all our activities like development, testing, deploying to production, etc., to achieve **reliability** and **reproducibility**.
- It should be easy to share the same environment set up with (new) employees and colleagues.


### Reasons for Docker's🐳 existence
- Docker solves all the above problems by providing a **"independent, standardized" application package environment** using containers and images. Docker makes it easy to install and run software without worrying about setup or dependencies and ensures that everyone working on a project gets the same environment. 
- Docker makes environment sharing easy. i.e., it is portable. 
- When using Docker, we don't have to install development tools and production tools locally in our machine except for Docker (for example, NodeJS, Python, PHP, MongoDB, Nginx, etc., need not be installed locally). Docker has them configured in its images and containers.

We will read more about images and containers later. For now, understand that images and containers are the basic building blocks of Docker.

🥳 Congratulations! You have learned why we use Docker. Next, we will see what Docker is.