---
layout: post
title: SCS215 Servo Calibration
---

ARIPS Arm v2 is built with Feetech SCS215 servos which are a cheap but powerful alternative to the Dynamixel AX-12A. Just like the Dynamixel servos, the SCS215 provide positional and torque feedback over a serial bus interface. The positional resolution is 10 bit, i.e. 1024 steps. With a rotational range of about 300 degrees, this means about 0.3 deg per raw step. However, the internal potentiometer seems not to provide fully linear feedback w.r.t. the rotation angle, and also each individual servo has a slightly different angular offset.

Therefore I designed and 3d-printed a servo calibration plate with blades at 10 deg distance.

![3D printed servo calibration plate]({{ site.baseurl }}/images/calibration_plate.jpg)

By manually adjusting the input position to let the calibration arrow point exactly at a particular blade, I created the curve resembling the raw value <-> rotation relation for every single servo.

![Calibration curve for servo #2]({{ site.baseurl }}/images/servo_calibration.png)

The arm controller node takes a [lookup table of these raw angle <-> angle pairs](https://github.com/jgdo/arips_ros/blob/master/arips_launch/config/scs_servo_params.yaml) and interpolates the values in between. 

The 3D OpenSCAD and STL files for the calibration plate can be downloaded at [https://www.thingiverse.com/thing:3116512](https://www.thingiverse.com/thing:3116512).

