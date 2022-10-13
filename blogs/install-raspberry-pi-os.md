---
layout: default
title: Install Raspberry OS (64-bit) on a MicroSD card and use it to boot the Raspberry Pi
---

[« Home](https://jedsadasrijunpoe.github.io/)

# Install Raspberry OS (64-bit) on a MicroSD card and use it to boot the Raspberry Pi

In this blog, I will install **Raspberry OS (64-bit)** on a **MicroSD card** and use it to boot the Raspberry Pi (RPi) SBC (operating in headless mode). Use RPi 3B or RPi 4B board with a MicroSD (8GB minimum or up to 32GB).

## Install Raspberry OS (64-bit) on a MicroSD card

Download [OS images](https://www.raspberrypi.com/software/operating-systems/) for RPi

![raspberrypi-1-1](/images/raspberry_pi/raspberry_pi_1-1.png)

Download [Raspberry Pi Imager](https://www.raspberrypi.com/software/)

![raspberrypi-1-2](/images/raspberry_pi/raspberry_pi_1-2.png)

Open *Raspberry Pi Imager*

![raspberrypi-1](/images/raspberry_pi/raspberry_pi_1.png)

Select **Operating System** as OS image for RPi that you downloaded and select **Storage** as your microSD card

![raspberrypi-2-1](/images/raspberry_pi/raspberry_pi_2-1.png)  
![raspberrypi-2-2](/images/raspberry_pi/raspberry_pi_2-2.png)  
![raspberrypi-2-3](/images/raspberry_pi/raspberry_pi_2-3.png)  
![raspberrypi-2-4](/images/raspberry_pi/raspberry_pi_2.png)

Click **Advanced Options** at bottom right
- Set hostname (default is raspberrypi.local)
- Enable SSH for operating in headless mode
- Set username and password
- Config wireless LAN for connecting to Wi-Fi

![raspberrypi-3](/images/raspberry_pi/raspberry_pi_3.png)

Click Write to install OS image to MicroSD card

![raspberrypi-5](/images/raspberry_pi/raspberry_pi_5.png)

## Boot the Raspberry Pi (RPi) SBC (operating in headless mode)

Insert microSD card to Raspberry Pi and boot it up. After that we are going to operate in headless mode with SSH. We need to use a computer with the same network as Raspberry Pi and use command `ssh [username]@[hostname]` and enter password 

![boot-raspberrypi-1](/images/raspberry_pi/raspberry_pi_6.png)