---
layout: post
title: Object Detection and Grasping
---

Using its [arm]({% post_url 2019-8-25-ARIPS-Arm %}), ARIPS can grasp and move around small objects. Here is a simple demonstration, where a detected object is picked and dropped back onto the floor. In the top left corner the rviz view from the onboard Kinect's perspective of the scene is shown. The detected object is marked as a green cube. Note how the calibration plate is fully visible to properly [compute the Kinect's current pose]({% post_url 2019-8-26-Kinect-Pose-Calibration %}).

<iframe width="640" height="360" src="https://www.youtube.com/embed/eVmLF2kNQsg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Object detection is performed on the Kinect's depth data only. The general approach is based on this [Cluster Extraction PCL Tutorial](http://pointclouds.org/documentation/tutorials/cluster_extraction.php#cluster-extraction). After extracting the ground plane, the remaining points are clustered into objects and filtered by their size and position relative to the robot. Note that currently there is no object recognition, so everything standing out from the ground plane is considered as a cube. Also orientation is ignored. The detection code keeps track of the objects by maintaining a simple list and creating a new entry for every newly detected object when the closest distance to every previous object is greater than a fixed threshold. To avoid too much noise in the 3d position, the average between previous and current detection is taken. The (ugly) code can be found [here](https://github.com/jgdo/arips_ros/blob/master/arips_groundplane_segmentation/src/main.cpp).

