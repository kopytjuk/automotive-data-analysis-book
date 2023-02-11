# Coordinate systems

## Cartesian coordinate system

### Introduction

This system is the first system we hear about in high school. First it is taught in terms of *x,y*-graphs where pupils enter pairs of numbers in a 2-D system. Later, we learn the term *function* which is can be represented graphically as a curve in this system.

A bit about history: Cartesian coordinates are named for René Descartes whose invention of them in the 17th century revolutionized mathematics by providing the first systematic link between geometry and algebra. Using the Cartesian coordinate system, geometric shapes (such as curves) can be described by equations involving the coordinates of points of the shape.[^wiki_cartesian_system]

### Left- vs. right-handed

In 2-D system, the position of x and y is fixed for many people, where the y axis is usually pointed toward the north. For a 3-D system however, there are multiple definitions:

<p align="center">
  <img src="cartesian_coordinate_system_handedness.svg" />
</p>

<figcaption><center>

**Figure 1**: Left-handed coordinates on the left, right-handed coordinates on the right. [Image from Wikipedia](https://en.wikipedia.org/wiki/Right-hand_rule#/media/File:Cartesian_coordinate_system_handedness.svg)

</center></figcaption>

For **right-handed** coordinates, the right thumb points along the z-axis in the positive direction and the curling motion of the fingers of the right hand represents a motion from the first or x-axis to the second or y-axis. When viewed from the top or z-axis the system is counter-clockwise.[^wiki_right_hand_rule] Robotic applications and frameworks such as ROS, use the right hand-rule.

For left-handed coordinates, the left thumb points along the z-axis in the positive direction and the curling motion of the fingers of the left hand represent a motion from the first or x-axis to the second or y-axis. When viewed from the top or z-axis the system is clockwise.[^wiki_right_hand_rule]

## Spherical coordinate system

Spherical coordinate system is used across a a wide palette of applications, besides astronomy and geo-informatics, it is essential for automotive applications, too. A RADAR or LIDAR sensor output their readings by providing the range, azimuth- and elevation-angle to the object of the detection. This section provides a short overview over notation, characteristics and commonly used coordinate transformations.

... WIP


## References

[^wiki_cartesian_system] Wikipedia - Cartesian Coordinate System, [link](https://en.wikipedia.org/wiki/Cartesian_coordinate_system)

[^wiki_right_hand_rule] Wikipedia - Right hand rule, [link](https://en.wikipedia.org/wiki/Right-hand_rule)

[^ros_rep103] ROS REP103 - Standard Units of Measure and Coordinate Conventions, [link](https://www.ros.org/reps/rep-0103.html#coordinate-frame-conventions)

