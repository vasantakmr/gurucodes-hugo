---
title: Virtual Machines vs Containers
lastmod: 2019-04-16T09:12:30-08:00
draft: false
description: Key terms and concepts related to the Some Description
weight: 2
emoji: ⚙️
free: true
---

Problems with virtual machines:

- Standard machine running on top of our machine. So it results in a lots of wasted resources like hard drive, cpu, ram etc and tends to be slow.

Pros and Cons of Virtual Machines:

Pros:

Separated environments. 

Environment specific configurations are possible. 

Environments configurations can be shared and reproduced reliably. 

Cons: 

Redundant duplication, waste of space.

Performance can be slow, boot times can be long.

Reproducing on another computer/server is possible but may still be tricky.


| Docker Containers | Virtual Machines |
|--|--|
| Low impact on OS, very fast, minimal disk space usage. | Bigger impact on OS, slower, higher disk space usage |
|Sharing, rebuilding and distribution is easy.|Sharing, re-building and distribution can be challenging|
|Encapsulate Apps/environments instead of "whole machines"|Encapsulate "whole machines" instead of just apps/environments.|
