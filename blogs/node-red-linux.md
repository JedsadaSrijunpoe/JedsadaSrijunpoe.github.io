---
layout: default
title: Install/run Node-RED using Linux
---

[« Home](https://jedsadasrijunpoe.github.io/)

<h1>Install/run Node-RED using Linux</h1>

Node-RED is a programming tool for wiring together hardware devices, APIs and online services in new and interesting ways.

It provides a browser-based editor that makes it easy to wire together flows using the wide range of nodes in the palette that can be deployed to its runtime in a single-click.

---

# Node-RED Installation on Ubuntu
## Install curl and Node (v16.x)

```ShellSession
$ sudo apt install -y curl
```

![nodered-install-1](/images/node_red/node-red-install-1-1.png)

```ShellSession
$ curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
```

![nodered-install-2](/images/node_red/node-red-install-1-2.png)

```ShellSession
$ sudo apt install -y nodejs
```

![nodered-install-3](/images/node_red/node-red-install-2-1.png)

---

## Install [Node-RED locally](https://nodered.org/docs/getting-started/local)

```ShellSession
$ sudo npm install -g --unsafe-perm node-red
```

![nodered-install-4](/images/node_red/node-red-install-3-1.png)

```ShellSession
$ node-red
```

![nodered-install-5](/images/node_red/node-red-install-4.png)

Open in the browser: <http://127.0.0.1:1880/>

![mynodered1](/images/node_red/mynodered1.png)