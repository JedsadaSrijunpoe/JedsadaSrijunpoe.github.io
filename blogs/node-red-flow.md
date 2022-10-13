---
layout: default
title: Create a Node-RED flow for publishing and subscribing messages
---

[« Home](https://jedsadasrijunpoe.github.io/)

# Create a Node-RED flow for publishing and subscribing messages

In this blog, we will create a Node-RED flow for publishing and subscribing messages to a public MQTT broker.

![complete flow](/images/node_red/mynodered9.png)

---

## 1. Add an inject node

![inject node](/images/node_red/mynodered2-1.png)

Edit its properties:

![inject node properties](/images/node_red/mynodered3.png)

Each inject node generates a message that you can edit some properties such as node name, message payload, and additional user-defined properties.

In this case, we use timestamp as a message payload and inject once after 0.1 seconds, then repeat for every 5 seconds.

---

## 2. Add a function node

![function node](/images/node_red/mynodered6-1.png)

Edit its properties:

![inject node properties](/images/node_red/mynodered7.png)

```js
// Convert the payload to a String object
msg.payload = new Date(msg.payload).toString();
return msg;
```

This JavaScript code is used to convert the incoming payload of the message (msg.payload) which is a timestamp value (in seconds) into a JavaScript Datestring.

---

## 3. Add a mqtt in node and a mqtt out node

![mqtt in node](/images/node_red/mynodered10-1.png)
![mqtt out node](/images/node_red/mynodered11-1.png)

Edit its properties:  
First, we need to **add new MQTT-broker config node** by clicking at this *pen icon* when edit mqtt in node properties.

![add new mqtt-broker1](/images/node_red/mynodered10-2.png)

We will test it by using Mosquitto public MQTT broker *"test.mosquitto.org"* with port 1883.

![add new mqtt-broker2](/images/node_red/mynodered8.png)

Edit **mqtt in** node properties:

![mqtt in node properties](/images/node_red/mynodered11.png)

Edit **mqtt out** node properties:

![mqtt out node properties](/images/node_red/mynodered10.png)

---

## 4. Add a debug node

![debug node](/images/node_red/mynodered15.png)

![complete flow](/images/node_red/mynodered9.png)

After we wire to connect all node together, we can click to **deploy** and see the **debug output**.

![debug output](/images/node_red/mynodered16.png)