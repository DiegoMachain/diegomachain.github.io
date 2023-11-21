---
layout: page
title: Projects
subtitle: Some projects
---


### Learning-based Articulated Object Mapping with the HoloLens
This project was carried out in the [Autonomous Systems Lab](https://asl.ethz.ch) at ETH Zurich.
The objective of this project was to create a 3D segmented mesh reconstruction of articulated objects with axis parameters of prismatic or rotational joints for robot simulators making use of the HoloLens 2. So we can close the gap between real and digital objects. 

In this project I used [Ditto](https://github.com/UT-Austin-RPL/Ditto), which is a learning-based method written in PyTorch that uses encoders-decoders as the network architecture in conjunction with the HoloLens to also be able to have an easy way for human interaction to double check the results from the automatic process. The structure of the project is as follows:

![](/assets/img/Process_HoloLens.png)

Where the process begins with two point clouds of the object, one before and one after interaction. These point clouds are recorded and sent from sent from the HoloLens to the server for preprocessing. Then Ditto plays a crucial part, and the point clouds are fused with an affine layer 

The HoloLens 2 was used as a scaner, sequence controller and visualizer of the results. The communication between the HoloLens 2 and the server for was done using ROS.


![](/assets/img/Ditto_Arch.png)


![](/assets/img/URDF_GIF.gif)


### Interactive Room Layout using Scene Graph Manipulation

In this project we developed an application to change the arrangement of furniture in a scan of a room using scene graphs. We worked exensively with meshes to manipulate vertices conrresponding to individual objects. We also addressed various challenges, such as mesh fixing due to imperfect scans, object collisions, texture management, and managing object relationships between objects.
The development was relying heavily on Trimesh and Open3d packages.

![](/assets/img/3dVision.png)

### Simulations Studies of Electron Lens Impact on Beam Parameters for Future Circular Colliders


I conducted simulations involving an electron lens designed for the Future Circular Collider at CERN. The primary objective of these simulations was to assess the impact of these lenses on the beams within the collider. The advantages offered by these colliders include the compensation of beam-beam effects, Landau damping, and collimation for halo particles. You can access the report for this project through this [link](https://cds.cern.ch/record/2635161?ln=es).

![](/assets/img/BEAM.png)


### PINNs for Solving PDEs

The objective of this project was to solve the one-dimensional heat equation with a feedforward dense neural network with tunable parameters

![](/assets/img/PINNs.png)

