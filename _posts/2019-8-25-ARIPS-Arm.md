---
layout: post
title: ARIPS Arm
---


The ARIPS Arm is a custom designed 3D-printed 5 DOF robot arm with a gripper at the end effector. It is built mainly with Feetech SCS215 servos, which are quite precise and have a positional feedback. 

| ![]({{ site.baseurl }}/images/arm_1.jpg)  |  ![]({{ site.baseurl }}/images/arm_2.jpg) |

## History ##
The above arm is actually the second version, the first one was made using conventional RC servos with custom electronics and controller. The first version had 5 wires per joint (2 for the motor and 3 for the positional potentiometer), resulting in 30 (!) wires in total, making the arm quite stiff and very prone to cable rupture. Additionally the arm contained some 3d-printed gears, which quickly wear off and the backlash increased over time, making the arm just wobbly and unstable, and of course harder to control. Controlling was done by an Arduino Duo board connected via [rosserial](http://wiki.ros.org/rosserial), but uncapable to store the large [ROS trajectory_msgs/JointTrajectory Message](http://docs.ros.org/melodic/api/trajectory_msgs/html/msg/JointTrajectory.html). Thus a custom trajectory message plus custom Arduino and PC ROS node software needed to be written and maintained. Not to mention the relatively large size of the controller board. 

Alltogether the ARIPS Arm v1 was hard to design, error-prone, hard to use and to maintain, less precise, and at the end even more expensive then the new arm using the SCS215 servos! For me this was a clear signal to rely more on industrial-made parts instead of trying to do build everything by myself.

![ARIPS Arm v1]({{ site.baseurl }}/images/arm_old.jpg)|
:---:|
ARIPS Arm v1 with custom actuators and gears|
