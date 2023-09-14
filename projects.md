---
layout: page
title: Projects
subtitle: Some projects
---


### Learning-based Articulated Object Mapping with the HoloLens
This project was done in the [Autonomous Systems Lab](https://asl.ethz.ch) at ETH Zurich.
The objective of this project was to create a 3D segmented mesh reconstruction of articulated objects with axis parameters of prismatic or rotational joints for robot simulators making use of the HoloLens 2. So we can close the gap between real and digital objects. 

In this project I used [Ditto](https://github.com/UT-Austin-RPL/Ditto), which is a learning-based method written with PyTorch that uses encoders-decoders as the network architecture.

The HoloLens 2 was used as a scaner, sequence controller and visualizer of the results. The communication between the HoloLens 2 and the server for was done using ROS.


![](/assets/img/URDF_GIF.gif)


### Interactive Room Layout using Scene Graph Manipulation

In this project we developed an application to change the arrangement of furniture in a scan of a room using scene graphs. We worked exensively with meshes to manipulate vertices conrresponding to individual objects. We also addressed various challenges, such as mesh fixing due to imperfect scans, object collisions, texture management, and managing object relationships between objects.
The development was relying heavily on Trimesh and Open3d packages.

![](/assets/img/3dVision.png)

### Simulations Studies of Electron Lens Impact on Beam Parameters for Future Circular Colliders

I performed simulations of an electron lens for the Future Circular Collider at [CERN](https://www.home.cern). The main porpose of the simulations was to see the effects of such lenses on the beams in the collider. The advantages of these colliders are a compensation of beam-beam effects, Landau damping and collimation for halo particlee. The report for this project can be found [here](https://cds.cern.ch/record/2635161?ln=es)

![](/assets/img/BEAM.png)

