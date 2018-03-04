---
layout: post
title:  "First Steps (Report from 2017, Part 1)"
date: 2018-02-20
---

We wanted to build a very simple prototype first, without too much planning. The aim was to quickly have something that can move, to get some experience with the basic building blocks and to have a starting point to build on.

This first “pre-prototype” only had the essential components:

- Raspberry Pi Zero W
- Two Lego Technic motors
- An L9110S motor driver board
- A powerbank for the Pi
- 3xAA batteries for the motors
- A perfboard with some connectors and a ULN2003 IC as an attempt to protect the GPIO pins (and maybe for later, to be able to drive things with higher voltage/current)
- An LED we can turn on and off as we please
- Some Lego and rubber bands to hold everything together (with limited success)

The two rear wheels were driven separately by the two motors, using PWM with the [PIGPIO library](http://abyz.me.uk/rpi/pigpio/index.html). We’we written a simple Python program that provides a sort of command-line remote control interface. We suspect that the method of SSH’ing into the Pi from a laptop, starting the script and then quickly typing “forward”, “left”, “right”, “stop” may not be ideal for challenges requiring quick reaction time like Pi-Noon, but it was good enough for now.

So, in summary, there was nothing terribly innovative about all this and even if this initial setup (hopefully!) doesn’t look anything like the final robot, it was a lot of fun to build. Also, this gave us some confidence to see how quickly we can put together something from scratch that works.

We also did some tests with streaming video from an attached camera and found that the lag was really bad (not sure if it was due to issues with the wifi connection or something else, we didn’t investigate further).

Once we were satisfied that it was working, we took the whole thing apart, hoping to move on to the next stage quickly and start building the “real” version. But before this we also took some spectacular videos (next time we should really have better lighting)!

<video controls>
    <source src="{{ "/assets/2018-02-20/video1.webm" | absolute_url }}" type="video/webm"/>
    <source src="{{ "/assets/2018-02-20/video1.mp4" | absolute_url }}" type="video/mp4">
</video>
