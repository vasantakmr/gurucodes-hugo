---
title: "What is Docker?"
lastmod: 2019-04-16T09:12:30-08:00
draft: false
description: Understanding docker.
weight: 2
emoji: 📜
free: true
---


Admit it: We all have used the line "It works on my machine." And we wished to share our machine with others along with the code. But what are the ways to do that? 

Either we should develop our application in a separate virtual machine or in a place that maintains isolation with our local OS. So, using virtual machines, we can build our application in a completely isolated environment and share our virtual machine with others.

{{< figure src="/courses/docker/img/itworksonmymachine.webp" caption="It Works On My Machine" >}}


But is it a good choice? Virtual machines are not lightweight. They consume a lot of resources. They run a complete OS including its own kernel, hard disk, ram on top of our local OS and hence have a noticeable lag in performance. If you want to run 2-3 apps simultaneously, our local machine will have to run 2-3 virtual machines. 

### Pros and Cons of Virtual Machines
Pros:
- Separated environments.
- Environment-specific configurations are possible.
- Environments configurations can be shared and reproduced reliably.

Cons:
- Redundant duplication, waste of space.
- Performance can be slow, and boot times are long.
- Reproducing on another computer/server is possible but may still be tricky.

### Docker Introduction

Here is where Docker comes to rescue. Docker provides lightweight isolation using something called containers. Containers are a standardized unit of software that allows developers to isolate their app from their environment. Each container will not have its own kernel & other OS components. Instead, they rely on the local machine's kernel. These containers run on top of the Docker engine. Containers will contain only the necessary files, software, and dependencies to run the app correctly. Hence it consumes fewer resources and memory than virtual machines and provides much better performance. Containers are also portable and small in size. It will run exactly the same way in any machine.

Here's a quick comparison of Docker containers and Virtual Machines:
| Docker Containers | Virtual Machines |
|--|--|
| Low impact on OS, speedy, minimal disk space usage. |	More significant effect on OS, slower, higher disk space usage |
| Sharing, re-building, and distribution are easy. | Sharing, re-building, and distribution can be challenging. |
| Encapsulate Apps/environments instead of "whole machines" |	Encapsulate "whole machines" instead of just apps/environments. |


### Summary:
- Docker is a container technology. i.e., A tool for creating and managing containers.
- A container is a standardized unit of software—a package of code and dependencies to run that code. (eg: nodejs code + nodejs runtime)
- The container always gives the exact same application and execution behavior no matter where or by whom it gets executed.
- Docker simplifies the creation and managing of such containers.


In the next lesson, we'll read about Images and Containers.

