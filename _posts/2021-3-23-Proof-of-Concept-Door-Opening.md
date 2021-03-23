---
layout: post
title: Proof-of-Concept Door Opening
---

Finally, I got a working proof of concept of autonomous door opening. This is the first step to enable ARIPS navigate in my appartement even if a room door is closed.

<iframe width="480" height="720" src="https://www.youtube.com/embed/ZwGs850yUls" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Hardware overview
To open a door, a 3D printed door handle gripper has been designed. It has a linear actuator driven by a Feetech SCS009 servo. To amplify the pulling force, the servo first drives a worm gear, than the gripper. Since a full movement of the gripper needs multiple servo turns, I took the positional potentiometer from inside the servo and mounted it on the inner gear. The gripper is mounted on an additional rig at door handle height. The kinect is pointed upwards to detect the door handle position.

![Robot mount]({{ site.baseurl }}/images/door/IMG_20210323_173937.jpg) | ![Handle gripper]({{ site.baseurl }}/images/door/IMG_20210323_173901.jpg)
:-------------:|:-------------:
![Start opening door]({{ site.baseurl }}/images/door/IMG_20210323_174055.jpg) | ![Pull down handle]({{ site.baseurl }}/images/door/IMG_20210323_174140.jpg)


# Software

The robot needs to drive right below the door handle to successfully grab it. To know where the door handle is, a door handle detection has been implemented using the RGB image of the kinect. 3D depth data is unfortunately unavailable since the distance to the kinect is too low. For the detection, a [U-Net](https://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/)-inspired convolutional neural network has been trained. The networks outputs two heatmaps per RGB image, one for each side of the door handle. The final position is the location of the maximum value of the heatmap. 

The training data was collected manually and annotated using a custom python tool. Currently it consists of about 1200 door handle images plus 300 images without a door handle. For training, the images are augmented with random brightness and contrast adjustments and gaussian noise.

![Some annotated door handle]({{ site.baseurl }}/images/door/annotated_door_handle.png) | ![Some other annotated and autgmented door handle]({{ site.baseurl }}/door/images/augmented_door_handle.png)
:-------------:|:-------------:
Some annotated door handle | Some other annotated and autgmented door handle
