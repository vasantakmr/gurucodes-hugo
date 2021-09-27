---
title: "Introduction: Why Docker Exists?"
lastmod: 2019-04-16T09:12:30-08:00
draft: false
description: Some Description
weight: 1
emoji: 📜
chapter_start: What is Docker, really?
free: true
---

**Docker: Why It Exists?**

Lets first understand why docker exists.

What exact problem is Docker trying to solve?

- Developers work on different development and production environments.
Example: Lets say I developed nodejs app in local machine with nodejs 14 installed. And production environment has nodejs12 installed. This might cause issues. Or because of some setting my app is working locally and it might not work in the production environment.
We want to build and test exactly the same environment as we later run our app in.
- Different development environments within a team/company have different environment setup and when working on same project there might be different issues raised because of different environment setups of developers.
- Clashing versions/tools between different projects. Same person might have to work with different versions of python or some other tools. And switching versions every time is a pain.
- It should be easy to share a common development environment setup with (new) employees and colleagues.
- We want **reliability** and **reproducibility** in environments of software development.
- We want to have the **exact same environment for development and production**. This ensures that it works exactly as tested.

Docker solves this problem by providing a **"independent, standardized" application package environments** using containers and images.

So Docker ensures that everyone working on a project gets the exact same environment. Docker makes the environment sharing easy. i.e., it is portable. And using docker we don't have to install development tools and production tools locally (example: nodejs, python, php, mongodb, nginx etc need not be installed locally). Docker have them configured in its images and containers. We will read more about images and containers later. For now just understand that images and containers are the basic building blocks of Docker.