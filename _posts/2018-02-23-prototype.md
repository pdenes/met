---
layout: post
title:  "Introducing the MRV0.2"
date: 2018-02-23
---

The new MRV0.2 (the second [“quick prototype”]({{ site.baseurl }}{% post_url 2018-02-22-harder-than-expected %})) is a huge improvement on the MRV0.1 ([“pre-prototype”]({{ site.baseurl }}{% post_url 2018-02-20-first-steps %})): it has motors for each wheel and each one can turn itself so the rover can move in (almost) any direction. However, the major disadvantage of the MRV0.2 is that the whole structure for the wheels is very weak, resulting in little mobility and many accidents (see the video).

![]({{ "/assets/2018-02-23/mrv_0_2-1_m.jpg" | absolute_url }})

![]({{ "/assets/2018-02-23/mrv_0_2-3_m.jpg" | absolute_url }})

<img src="{{ "/assets/2018-02-23/mrv_0_2-2_m.jpg" | absolute_url }}" class="half"/>

Despite its imperfections, this new prototype allowed us to start developing more sophisticated motor and servo control. Figuring out how to turn smoothly and using different methods (e.g. rotate in place, change direction while moving without turning the body, or turning like a car, etc.) will be a fun challenge!

<p>
<video controls style="width:640px;height:360px;">
    <source src="{{ "/assets/2018-02-23/video3.webm" | absolute_url }}" type="video/webm"/>
    <source src="{{ "/assets/2018-02-23/video3.mp4" | absolute_url }}" type="video/mp4">
</video>
</p>

For PWM, we’ve switched to a new controller board, with the incredibly useful PCA9685 chip. This is a 16-channel PWM driver that can be controlled via I2C. We use it to offload the low-level PWM generation task from the Pi. It also simplifies wiring as it only needs three wires from the Pi and the board comes with nice servo connectors. With some experimenting we found that setting the frequency to 60Hz, it can control both servos and motors – with plenty of room to add more!

Adafruit has very nice [documentation](https://www.adafruit.com/product/815) and they also provide a [Python driver](https://github.com/adafruit/Adafruit_Python_PCA9685/).

Ours is a cheap “clone” from eBay (the chip looks genuine and the board itself is really just a simple breakout for the chip, so it probably doesn’t make much difference, and it works fine – but the labels on the back look a bit odd):

<img src="{{ "/assets/2018-02-23/pca9685_1_m.jpg" | absolute_url }}" class="half"/>

<img src="{{ "/assets/2018-02-23/pca9685_2_m.jpg" | absolute_url }}" class="half"/>
