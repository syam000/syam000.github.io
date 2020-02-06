---
layout: post
title:  "How to light up your room using nitlite and learn something..(Part 1)"
date:   2020-02-06 12:43:16 +0800
categories: iot
---

![](/assets/nitlite_part_1_post_1.jpeg)
by Saya Kimura @ Pexels

I have this idea of creating an IoT application and write a blog about it for long time. Now I am fulfiling that dream with this write up :D
So this is going to be a technical blog, which covers hardware & software. I am not an expert in any of these but I will try to explain in a way that everybody can understand :)

**What is it about?**

I have named this project as nitlite. So basically what is does is controlling a light via internet. It’s not something new at this point in time, but still it’s relevant to talk about it to make people understand. I am covering few technologies in this topic, such as nodejs, iOS, android, mqtt, REST, IoT, nodemcu etc. Yes these are the buzz words you gonna get familiarize with this story series. I hope anyone of you could follow it and make it happen in your own way.

**How does it work?**

I could explain the whole process like this; the mobile app sends turn on/off commands to a backend server , then server notifies the LCU (Ligh Control Unit) about the command and LCU pass appropriate signal to the light accordingly. Then the light will be turned on/off. Thats it :)

Lets go bit more technical :)

So here what I built.

![](/assets/nitlite_part_1_post_2.png)

* A Backend Server — nodejs app + MongoDB — Server
* Client Apps (iOS/Android) — Client
* A Light control unit using nodemcu — LCU

The server serves the clients – mobile app and the edge devices – light control unit. The server exposes interfaces via [REST](https://www.restapitutorial.com/lessons/whatisrest.html) and [MQTT](http://mqtt.org/). Clients can communicate to the server either via REST. The server is the central unit of communication between the clients. The iOS/android clients act as the front-end of the whole system. The users will be able to control the light using these apps. Next is the light control unit (LCU), is the hardware component directly connected to the light. The communication between the mobile app and server is via REST. In the case of server to LCU communication, MQTT protocol is being used.


**Next steps**

In the next post I will explain about the implementation in detail.
