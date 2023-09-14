---
layout: page
title: Projects
subtitle: Some projects
---


### Learning-based Articulated Object Mapping with the HoloLens
This project was done in the [Autonomous Systems Lab](https://asl.ethz.ch) at ETH Zurich
The objective of this project was to create a 3D segmented mesh reconstruction of articulated objects with axis parameters of prismatic or rotational joints for robot simulators making use of the HoloLens 2. So we can close the gap between real and digital objects. 

In this project I used [Ditto](https://github.com/UT-Austin-RPL/Ditto), which is a learning-based method written with PyTorch that uses encoders-decoders as the network architecture.

The HoloLens 2 was used as a scaner, sequence controller and visualizer of the results. The communication between the HoloLens 2 and the server for was done using ROS.



![](/assets/img/URDF_GIF.gif)


### 3D vision

In this project we developed an application to change the arrangement of furniture in a scan from a room. We worked exensively with meshes to manipulate vertices conrresponding to individual objects. We also addressed various challenges, such as mesh fixing due to imperfect scans, object collisions, texture management, and managing object relationships between objects.

### Simulations Studies of Electron Lens Impact on Beam Parameters for Future Circular Colliders

Simulations project performed at CERN, [CERN-THESIS-2018-122](https://cds.cern.ch/record/2635161?ln=es)