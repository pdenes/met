---
layout: post
title:  "No More Prototyping"
date: 2018-04-29
excerpt: "The last few weeks leading to Pi Wars were extremely busy. After a long time spent prototying and experimenting freely, our team now realised there wasn’t much time left and we were rushing to finish building a “final” version of the robot, suitable for the competition.<br/>We didn’t have any time to update the blog, so this post is slightly late… More will follow!"

---

The last few weeks leading to Pi Wars were extremely busy. After a long time spent prototying and experimenting freely, our team now realised there wasn’t much time left and we were rushing to finish building a “final” version of the robot, suitable for the competition.

We didn’t have any time to update the blog, so this post is slightly late… We’re still catching up, so more posts will follow about the competition!

![]({{ "/assets/2018-04-29/layout.png" | absolute_url }})

In theory, the plan was clear and straightforward: we learned a lot from the prototypes and knew what worked, what needed changing, which features were essential, and which ones could be left out or simplified. But this “final build” essentially meant a complete rebuild of the robot and every detail of this had to come together just right, with very little or no time to test.

So here is a list of all the final components:

#### **MOSS** – **MO**bility **S**y**S**tem

<!-- ![]({{ "/assets/2018-04-29/MOSS.jpg" | absolute_url }}) -->

<a href="{{ "/assets/2018-04-29/MOSS.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/MOSS.jpg" | absolute_url }}" class="half left"/></a>

The **MOSS** has four identical units: two at the front, and two at the back, all attached at equal distances from the center of the rover’s body. Each unit comprises a drive motor (N20 gear motor, 200 RPM), a steering servo (ES08MA, metal gears) and a wheel.

<a href="{{ "/assets/2018-04-29/MOSS_assembled.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/MOSS_assembled.jpg" | absolute_url }}" class="quarter right"/></a>

The servo rotates the whole motor holder with the center of rotation going right through the middle of the wheel. Inside the servo holder there is a small ball bearing which provides a very solid rotating platform: the motor holder and the servo shaft are both connected to its inner ring, so the servo doesn’t need to directly support any weight. The motor holder also provides a conduit for the cables.



(This design is an improved version of the one used for the [MRV0.3]({{ site.baseurl }}{% post_url 2018-03-04-mrv_0_3 %}): the wheels and the wheel holders are slightly smaller and lighter. The servo holder is much smaller and the servo - ball bearing connection is much more solid. The servos are the same, but the motors are twice as fast.)

The fully assembled version also has an encoder wheel (a cylinder with holes) and an optical sensor attached to the motor holder. The plan was to use these for speed measurement, but the rest of the required parts were not completed in time.

<div class="divider"></div>



#### **CBSU** – **C**entral **B**ody **S**upport **U**nit

<!-- ![]({{ "/assets/2018-04-29/CBSU.jpg" | absolute_url }}) -->

<a href="{{ "/assets/2018-04-29/CBSU.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/CBSU.jpg" | absolute_url }}" class="half left"/></a>

The **CBSU** is the frame that holds all the other parts of the body together: it has a flat, octagonal “deck” with two “towers” on each side, where the “legs” (not shown on the picture) with the **MOSS** units are attached. The **PM-1** (battery holder) is attached below the deck. Sensors or special attachments are connected to the front and all the other electronics units sit on the top.

<div class="divider"></div>



#### **PM-1** – **P**ower **M**odule **1**

<!-- ![]({{ "/assets/2018-04-29/PM-1.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/PM-1.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/PM-1.jpg" | absolute_url }}" class="half left"/></a>

The **PM-1** contains 2 (in series) + 1 18650 LiIon cells and protection circuits, providing two separate voltages (nominal 3.7V for the electronics and 7.4V for the motors). This separation ensures the electronics is isolated from any noise from the motors.

**PM-1** also provides direct connections to the individual battery terminals: these can be used for battery charge monitoring (not implemented yet).

<div class="divider"></div>



#### **P-CAMS** – **P**ower **C**onversion **A**nd **M**anagement **S**ystem

<!-- ![]({{ "/assets/2018-04-29/PCAMS.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/PCAMS.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/PCAMS.jpg" | absolute_url }}" class="half left"/></a>

The **P-CAMS** sits on the deck, directly above the **PM-1**. It has two DC-DC converters: one fixed 5V boost converter for the electronics and a variable buck-boost converter to provide about 6V for the motors and servos. (The rover is turned on by connecting the two connectors of **PM-1** to the **P-CAMS**.)

The **P-CAMS** also has outputs that could be connected directly to the **SIPS** for battery charge monitoring (it also has a voltage divider to scale down the voltage from the 2S cells), but this wasn’t used at the end.

<div class="divider"></div>



#### **ACF-MAS** – **A**ctuator **C**ontroller **F**or **M**otors **A**nd **S**ervos

<!-- ![]({{ "/assets/2018-04-29/ACF-MAS.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/ACF-MAS.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/ACF-MAS.jpg" | absolute_url }}" class="half left"/></a>

The **ACF-MAS** is responsible for driving the motors and the servos: it comprises a PCA9685 board with 16 PWM outputs and two DRV8833 2-channel motor drivers with motor connectors facing left and right. The servos are connected directly to the PCA9685 board connectors. The **MECCAPU** controls the **ACF-MAS** using I2C.

<div class="divider"></div>



#### **MECCAPU** – **M**ars **E**xploration **C**entral **C**omputing **A**nd **P**rocessing **U**nit

<!-- ![]({{ "/assets/2018-04-29/MECCAPU.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/MECCAPU.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/MECCAPU.jpg" | absolute_url }}" class="half left"/></a>

The **MECCAPU** (a Raspberry Pi Zero W) is responsible for the overall control of the rover. Apart from the built-in WiFi (set up as an access point), it also includes a receiver for direct remote control from Earth (a dongle for a Rock Candy PS3 controller). The main control program running on the **MECCAPU** also provides telemetry (sensor data, current speed and orientation, additional debugging from autonomous controller programs) that can be processed by a visualiser program running in the control center on Earth (or a laptop that connects to the rover’s WiFi).

<div class="divider"></div>



#### **CREMCOAM** – **C**entral **RE**lay **M**odule for **C**onnection **O**f **A**ll **M**odules

<!-- ![]({{ "/assets/2018-04-29/CREMCOAM.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/CREMCOAM.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/CREMCOAM.jpg" | absolute_url }}" class="half left"/></a>

The **CREMCOAM** sits between the **MECCAPU** and the **SIPS**. It looks very simple but its role is vital: it connects all the electronics modules together. It connects the serial pins of the **MECCAPU** to the **SIPS** via a 5V – 3.3V level shifter and also provides a connector to the **ACF-MAS** (I2C). It receives the 5V supply from the **SIPS** and provides a power connector to the **MECCAPU**.

<div class="divider"></div>



#### **SIPS** – **S**ensor **I**nformation **P**rocessing **S**ubsystem

<!-- ![]({{ "/assets/2018-04-29/SIPS.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/SIPS.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/SIPS.jpg" | absolute_url }}" class="half left"/></a>

The **SIPS** (shown in the right of the picture, with the half-assembled **FAROS** attached) is responsible for low-level real-time tasks. It’s Arduino Pro Mini clone running at 5V. Currently it only handles distance sensor measurement data, but the orignal plan also included speed measurement from the optical sensors on the wheels and battery charge monitoring. It can also show some very simple status information with an integrated LED using three different blinking modes. The **SIPS** is connected via **CREMCOAM** to the **MECCAPU** using the serial interface.

<div class="divider"></div>



#### **FAROS** – **F**rontal **AR**ray **O**f **S**ensors

<a href="{{ "/assets/2018-04-29/FAROS.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/FAROS.jpg" | absolute_url }}" class="half left"/>

The **FAROS** is an extra attachment that can be connected to the front of the **PM-1**. It has three VL53L0X Time-of-Flight laser-ranging sensors and provides distance measurements at the front and 45 degrees left-right. It connects to the **SIPS** using I2C.

<div class="divider"></div>



#### **SOGU** – **S**pherical **O**bject **G**rabber **U**nit

<!-- ![]({{ "/assets/2018-04-29/SOGU.jpg" | absolute_url }}) -->
<a href="{{ "/assets/2018-04-29/SOGU.jpg" | absolute_url }}"><img src="{{ "/assets/2018-04-29/SOGU.jpg" | absolute_url }}" class="half left"/></a>

The **SOGU** is another extra attachment that connects to the front of the rover. As its name suggests, it’s specially designed to *grab spherical objects*, for example golf balls. The ring can be lifted up and down using a servo, and it’s intentionally loosely attached so that it can move around a bit when moving on uneven terrain or slopes. 

<div class="divider"></div>

---

<div class="divider"></div>



And finally, here is the fully assembled “final” version of the rover!

<a href="{{ "/assets/2018-04-29/ghost1.jpg" | absolute_url }}">![]({{ "/assets/2018-04-29/ghost1.jpg" | absolute_url }})</a>

<p>
<video controls>
    <source src="{{ "/assets/2018-04-29/ghost.webm" | absolute_url }}" type="video/webm"/>
    <source src="{{ "/assets/2018-04-29/ghost.mp4" | absolute_url }}" type="video/mp4">
</video>
</p>

Comparing it with the carcass of the MRV0.3 prototype:

<a href="{{ "/assets/2018-04-29/MRV_ghost.jpg" | absolute_url }}">![]({{ "/assets/2018-04-29/MRV_ghost.jpg" | absolute_url }})</a>
