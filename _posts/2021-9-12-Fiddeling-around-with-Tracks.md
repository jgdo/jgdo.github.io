---
layout: post
title: Fiddeling around with Tracks
---

Arips always had problems with overcoming small steps and bumps as they occur on door edges if the floor of different rooms isn't exactly the same height. Especially the passive caster wheel would often get stuck on the edge. I tried different caster wheel sides and rubber types for the main wheels, but no approach was satisfactory. It even happened that the robot completely tipped over the rear caster wheel while doing rapid back and forth movement. Since I want it to be mechanically safe no matter what the software does with the motors, I decided to put the robot on tracks instead. Ideally they would provide a stable contact area without the danger of falling over in any direction. Unfortunately this didn't go to well either, so eventually I ended up mounting the previous differential drive and slightly improving the caster wheel again.


I went for the 57518 Lego Tracks, since the length can be easily adjusted and barely bend, there is no need for support wheels in between. I designed and 3d-printed the wheels and the mounting brackets such that the existing EMG30 motors and the MD25 board could be reused. For a better grip especially on door edges I gued felt peds on each on each track link. 


![Mounted lego tracks]({{ site.baseurl }}/images/tracks/tracks_view_side.jpg)| ![Tracks with felt pads]({{ site.baseurl }}/images/tracks/tracks_view.jpg)
:-------------:|:-------------:
Mounted lego tracks | Tracks with felt pads

For a better grip especially on door edges I gued felt peds on each on each track link. 

# Problems with tracks

With the tracks, the robot way standing way more stable on the ground, there was no way it could tip itself over by extreme motor commands. But there were two major problems with this setup:
 * The rotation center was not the robot center anymore, but the center of mass instead, which is about 7 cm behind the robot center. This completely ruined the  assumption that the round robot can always rotate in place without collision, requiring more sophisticated navigation software.
 * The tracks cannot be used on the carpet at all! Without the pads the tracks would slip at door edges. But with the pads, the tracks would completely block the motors when the robot tries to rotate in place on the carpet. 

![Stuck on carpet]({{ site.baseurl }}/images/tracks/on_carpet.jpg)

This issues render the track approach unusable for moving inside the appartment.


# New rear caster wheel and main wheels

One problem with the old caster wheel was that the rotation caster rotation axis was far away from the wheel axis. Therefor the floor contact point location varied a lot when the caster wheel was facing different directions, making the robot unstable.

![Caster wheel turned to back side when robot is driving forward. Robot is stable since center of mass is far away from outer contact point.]({{ site.baseurl }}/images/tracks/caster_back.jpg)
![Caster wheel turned to front side when robot is driving backward. Robot is unstable since center of mass is close to outer contact point. A sudden break would throw the robot over the wheel.]({{ site.baseurl }}/images/tracks/caster_front.jpg)

I moved the wheel axis closer to the caster rotation axis with some custom 3d-printed brackets which are mounted on top of the caster metal bracket. Also I printed a new, bigger wheel with TPU tires, hopefully helping it overcoming the door steps.

![]({{ site.baseurl }}/images/tracks/caster_1.jpg) | ![]({{ site.baseurl }}/images/tracks/caster_2.jpg)
:-------------:|:-------------:
|

TODO new wheels.

