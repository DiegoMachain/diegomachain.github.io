---
layout: post
title: Learning-based Articulated Object Mapping with the HoloLens
subtitle: 
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [HoloLens 2, Transformers, 3D Point Clouds]
---

This project was carried out in the [Autonomous Systems Lab](https://asl.ethz.ch) at ETH Zurich.
The objective of this project was to create a 3D segmented mesh reconstruction of articulated objects with axis parameters of prismatic or rotational joints for robot simulators making use of the HoloLens 2. So we can close the gap between real and digital objects. 

In this project I used [Ditto](https://github.com/UT-Austin-RPL/Ditto), which is a learning-based method written in PyTorch that uses encoders-decoders as the network architecture in conjunction with the HoloLens to also be able to have an easy way for human interaction to double check the results from the automatic process. The structure of the project is as follows:

![](/assets/img/Process_HoloLens.png){: .mx-auto.d-block :}

Where the process begins with two point clouds of the object, one before and one after interaction. These point clouds are recorded and sent from sent from the HoloLens to the server for preprocessing. Then Ditto plays a crucial part, and the point clouds are fused with an affine layer 

The HoloLens 2 was used as a scaner, sequence controller and visualizer of the results. The communication between the HoloLens 2 and the server for was done using ROS.

![](/assets/img/Ditto_Arch.png){: .mx-auto.d-block :}

Ditto is conformed of a an encoder called PointNet++, which encodes both input point clouds recorded by the HoloLens. The objective of this encoder is to create a subsampled point cloud that contains representative point features and they are invariant to rotations in the inputs. After these encoders, the resultant point features are then fused with an attention layer. Then these fused point features are decoded by two different decoders, one in charge of the mesh reconstruction and segmentation (Geometry Feature Decoder) and another in charge of the joint axis prediction (Motion Feature Decoder). Then they construct feature grid/planes by projecting and pooling the point features and query local features from the constructed feature grid/planes. Conditioning on local features, they use different decoders to predict occupancy, segmentation, and joint parameters with respect to the query points. From the final decoders we can obtain a mesh reconstruction, part segmentations into mobile and static parts, and a joint prediction.

These results are then sent back to the HoloLens for human correction of the joint axis prediction, this is performed using HoloLens interactive features as can be seen in the following figures:

![](/assets/img/Human_interaction.png){: .mx-auto.d-block :}

Finally, after the user double checks the resultant joint axis, the final results are then sent back to the server so we can take the final position and orientation of the joint axis to create a URDF model of the object. The following example represents a URDF model of my computer created with this model:


![](/assets/img/URDF_GIF.gif){: .mx-auto.d-block :}


The complete code for this project can be found [here]{https://github.com/DiegoMachain/ArticulatedObjectMapping/tree/main}