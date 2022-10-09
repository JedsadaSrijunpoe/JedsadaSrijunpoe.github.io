---
layout: default
title: Install/run Node-RED using Docker container
---

[« Home](https://jedsadasrijunpoe.github.io/)

<h1>Install/run Node-RED using Docker container</h1>

---

Node-RED is a programming tool for wiring together hardware devices, APIs and online services in new and interesting ways.

It provides a browser-based editor that makes it easy to wire together flows using the wide range of nodes in the palette that can be deployed to its runtime in a single-click.

# Node-RED Installation using Docker container

> To run a **Docker image**, a **Docker Engine** must be installed on Ubuntu.  
> Instructions for installing the Docker Engine on Ubuntu:  
> <https://docs.docker.com/engine/install/ubuntu/>

- using a [docker container](https://nodered.org/docs/getting-started/docker) to install Node-RED:

```ShellSession
$ docker run -it -p 1880:1880 -v $HOME/.node-red:/data \  
  --name mynodered nodered/node-red
```

![nodered-install-6](/images/node_red/node-red-install-5-1.png)

- Open in the browser: <http://127.0.0.1:1880/>

![mynodered1](/images/node_red/mynodered1.png)