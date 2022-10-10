---
layout: default
title: GUI-based MQTT client to publish messages or subscribe to a topic
---

[« Home](https://jedsadasrijunpoe.github.io/)

# GUI-based MQTT client to publish messages or subscribe to a topic

In this blog, I will show you how to use GUI-based MQTT client to publish messages or subscribe to a topic.

Examples of GUI-based MQTT Apps:
- [MQTT.fx](https://softblade.de/)
- [MQTT Explorer](https://github.com/thomasnordquist/MQTT-Explorer)
- [MQTTBox](https://github.com/workswithweb/MQTTBox)

I will use **MQTT Explorer** for this blog.

---

## Install MQTT Explorer

Go to <http://mqtt-explorer.com/>  
![mqtt-explorer-install-1](/images/mqtt_broker/gui_mqtt_client1.png)

Scroll down to the download and download for your platform  
![mqtt-explorer-install-2](/images/mqtt_broker/gui_mqtt_client2.png)

---

## Using MQTT Explorer to connect to a public MQTT broker

Open MQTT Explorer  
![mqtt-explorer-1](/images/mqtt_broker/gui_mqtt_client3.png)

I will use "test.mosquitto.org" as a public MQTT broker which is already created when you open the program.  
Server "test.mosquitto.org" Port 1883 then click connect.  
![mqtt-explorer-2](/images/mqtt_broker/gui_mqtt_client5.png)

---

## Subscribe to a topic

You can search for the topic that you want to subscribe. I use "test/1234/" as a topic.  
![mqtt-explorer-3](/images/mqtt_broker/gui_mqtt_client6.png)

---

## Publish messages to a topic

You can publish messages to a topic by enter the topic that you want to publish messages to.  
then, type the messages. You can choose to publish raw text, xml, or json and click publish.  
![mqtt-explorer-4](/images/mqtt_broker/gui_mqtt_client7.png)

The topic test/1234/msg will appear and you can see the message that you publish.  
![mqtt-explorer-5](/images/mqtt_broker/gui_mqtt_client8.png)
