---
layout: post
title: Changing the 28x1 clock speed
---

To reduce latency or increase clock speed for multiplexed displays, you can simply increase the clock speed of the 28x1, thus more commands can be executed per second.

This is placing the `setfreq` command at the very top of your code, i.e.

~~~asm
setfreq m8
~~~

This will change the clock speed to 8MHz, however because of the AQA complier, the actual clock speeds are shown in the below tables:

![ckspeeds](http://yuiko.xyz/f/59fk9o.png)
