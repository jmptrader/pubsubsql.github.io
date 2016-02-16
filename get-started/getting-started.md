---
layout: get-started
permalink: getting-started
title: Getting started | PubSubSQL
heading: Getting started with PubSubSQL
active: get-started
excerpt: "Getting started instructions"
search_omit: true
---

# Running the server

You can either run the server on your machine or you can use our publicly available **playground server** for **testing purposes**. If you use the public server keep in mind anyone can connect so don't put any confidential/private data into the database :)

### Public server

Public server is available at this endpoint: `192.99.101.169:7777`. Just follow the documentation for e.g. [Node JS](/docs/nodejs.html) and play!

### Using Docker
We've packed our PubSubSQL server in a lightweight Docker container - we don't want you to bother 
with installation and dependencies. To start coding and using the server just follow next two steps. 

We assume that you're familiar with Docker and have its environment ready.

1. Get the latest PubSubSQL image from DockerHub:

    ```shell
    $ docker pull pubsubsql/pss-server
    ```

2. Start PubSubSQL container:

    ```shell
    $ docker run -t -p 7777:7777 pubsubsql/pss-server
    ```

You're done and ready to rock, you can see PubSubSQL debug output in your terminal.

PubSubSQL is listening on `DOCKER_HOST:7777`.


-----
### Running the latest binary release

Latest release for **Linux, Windows and OSX** is available for [download here](https://github.com/pubsubsql/pubsubsql/releases/tag/v1.2.0) or just follow the instructions here:

#### OS X
``` bash
curl -L  https://github.com/pubsubsql/pubsubsql/releases/download/v1.2.0/pubsubsql-v1.2.0-darwin-amd64.tgz -o pubsubsql-v1.2.0-darwin-amd64.tgz
tar xzvf pubsubsql-v1.2.0-darwin-amd64.tgz
cd pubsubsql-v1.2.0-darwin-amd64
./pubsubsql
```

#### Linux
``` bash
curl -L  https://github.com/pubsubsql/pubsubsql/releases/download/v1.2.0/pubsubsql-v1.2.0-linux-amd64.tgz -o pubsubsql-v1.2.0-linux-amd64.tgz
tar xzvf pubsubsql-v1.2.0-linux-amd64.tgz
cd pubsubsql-v1.2.0-linux-amd64
./pubsubsql
```

#### Windows
- Download [https://github.com/pubsubsql/pubsubsql/releases/download/v1.2.0/pubsubsql-v1.2.0-windows-amd64.tgz](https://github.com/pubsubsql/pubsubsql/releases/download/v1.2.0/pubsubsql-v1.2.0-windows-amd64.tgz)
- Extract it
- Run `pubsubsql.exe`



----
### Building from source

If you want to run the server locally and build it yourself you'll need a functional Go environment, at least version 1.4.

1. Once you're set up just clone [https://github.com/pubsubsql/pubsubsql](our server repo) and build:

    ```shell
    $ go get github.com/pubsubsql/pubsubsql
    ```

3. You're ready! Running the server is simple as

    ```shell
    $ pubsubsql
    ```

----

# Connecting to the server

Once server is up and running (or you want to use our public playground server), just follow the docs for your favorite language:
- [Node JS](/docs/nodejs.html)
- [Go](/docs/go.html)
- [Java](/docs/java.html)
- [.NET](/docs/dotNet.html)
