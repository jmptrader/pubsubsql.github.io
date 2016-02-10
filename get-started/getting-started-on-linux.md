---
layout: get-started
permalink: getting-started-on-linux
title: Getting started on Linux | PubSubSQL
heading: Getting started on Linux
active: get-started
excerpt: "Getting started instructions for Linux users."
search_omit: true
---

You have a choice to install from source or simply running a Docker container.

# Running from Docker

We've packed our PubSubSQL server in a lightweight Docker container - we don't want you to bother 
with installation and dependencies. To start coding and using the server just follow next two steps. 

We assume that you're familiar with Docker and have its environment ready.

- Get latest PubSubSQL image from DockerHub:
```{r, engine='bash', count_lines}
$ docker pull pubsubsql/pss-server
```
- Start PubSubSQL container:
```{r, engine='bash', count_lines}
$ docker run -t -p 7777:7777 pubsubsql/pss-server
```
You're done and ready to rock, you can see PubSubSQL output in your terminal. PubSubSQL is listening on `DOCKER_HOST:7777`.

