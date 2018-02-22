---
layout: post
title:  "This is Harder than Expected (Report from 2017, Part 2)"
date: 2018-02-22
excerpt: After the first quick “pre-prototype” build our plan was to build a more robust second prototype and use it for experimenting with the basic mechanisms and control, and gradually improve it.
---

<img src="{{ "/assets/2018-02-22/motor_holder_s.png" | absolute_url }}" class="left"/> After the first quick [“pre-prototype”]({{ site.baseurl }}{% post_url 2018-02-20-first-steps %}) build, our plan was to build a more robust second prototype and use it for experimenting with the basic mechanisms and control and gradually improve it.

We were planning to use Lego Technic to quickly build the structure, with a few custom 3D-printed parts to attach the various non-Lego components (motors, circuit boards, bower bank). The idea was that this would allow us to quickly change things as we experiment and gradually replace the Lego parts as the final design emerges.

It’s just Lego, so how hard can it be…?

Well, it turned out to be much more complicated than we expected. But as this is our first robot, we already knew at the beginning that all this would be harder than we expect! So… it was all expected after all, so it’s all fine… I think…

<div class="divider"></div>

![]({{ "/assets/2018-02-22/servo_mount_s.png" | absolute_url }})
![]({{ "/assets/2018-02-22/powerbank_holder_s.png" | absolute_url }})

These “few custom 3D-printed parts” were not so easy to make. The dimensions of all the components were always a bit awkward, either too long or too short to match any standard Lego sizes. We always seemed to miss one more special part somewhere, or found something that didn’t fit. Designing the drive motor + steering servo assembly with Lego axles and gears was really difficult and it ended up being quite fragile. And of course, you typically only realise major mistakes in the design after many hours of printing!

So the “quick second Lego prototype” phase turned out to be countless hours (but a lot of fun!) spent with [OpenSCAD](http://www.openscad.org/), many more hours printing parts that won’t fit and many attempts to make the whole thing robust enough. Finally we ended up with a lot of custom Lego-compatible elements with only a very few actual original Lego parts!

<p>
<video controls style="width:640px;height:360px;">
    <source src="{{ "/assets/2018-02-22/video2.webm" | absolute_url }}" type="video/webm"/>
    <source src="{{ "/assets/2018-02-22/video2.mp4" | absolute_url }}" type="video/mp4">
</video>
</p>

![]({{ "/assets/2018-02-22/customlego_photo1_m.jpg" | absolute_url }})

![]({{ "/assets/2018-02-22/customlego_photo2_m.jpg" | absolute_url }})


