---
layout: get-started
permalink: getting-started-on-linux
title: Getting started | PubSubSQL
heading: Getting started with PubSubSQL
active: get-started
excerpt: "Getting started instructions"
search_omit: true
---

# Running from Docker

We've packed our PubSubSQL server in a lightweight Docker container - we don't want you to bother 
with installation and dependencies. To start coding and using the server just follow next two steps. 

We assume that you're familiar with Docker and have its environment ready.

- Get the latest PubSubSQL image from DockerHub:

    ```shell
    $ docker pull pubsubsql/pss-server
    ```

- Start PubSubSQL container:

    ```shell
    $ docker run -t -p 7777:7777 pubsubsql/pss-server
    ```

You're done and ready to rock, you can see PubSubSQL debug output in your terminal. PubSubSQL is listening on `DOCKER_HOST:7777`.

# Building from source

If you want to run the server locally and build it yourself you'll need a functional Go environment, at least version 1.4.

- Once you're set up just clone [https://github.com/pubsubsql/pubsubsql](our server repo) and build:

    ```shell
    $ go get github.com/pubsubsql/pubsubsql
    ```

- It should be ready to run! If by any chance pubsubsql binary was not automatically built, build it using

    ```shell
    $ go build github.com/pubsubsql/pubsubsql
    $ go install github.com/pubsubsql/pubsubsql
    ```

- Running the server is simple as

    ```shell
    $ pubsubsql
    ```
