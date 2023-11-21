---
layout: post
title: Learning-based Articulated Object Mapping with the HoloLens
subtitle: 
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/Thumb_semester.png
share-img: /assets/img/path.jpg
tags: [HoloLens 2, Transformers, 3D Point Clouds]
---

This project was carried out in the [Autonomous Systems Lab](https://asl.ethz.ch) at ETH Zurich.
My supervisors were [Mike Allenspach](https://asl.ethz.ch/the-lab/people/person-detail.MjA2NTUy.TGlzdC8yMDMwLDEyMDExMzk5Mjg=.html) and [Antonia Hüfner](https://asl.ethz.ch/the-lab/people/person-detail.MjkyMTM4.TGlzdC8yMDMwLDEyMDExMzk5Mjg=.html).

The objective of this project was to create a 3D segmented mesh reconstruction of articulated objects, specifying prismatic or rotational joint axis parameters for robot simulators making use of the HoloLens 2 for point cloud recordings and human interaction. This idea helps to closes the gap between real-world and digital objects.

In this project I used [Ditto](https://github.com/UT-Austin-RPL/Ditto), a PyTorch-based learning method employing encoders-decoders for mesh reconstruction and segmentation.  The project flow began with recording two point clouds of an object pre- and post-interaction, processed by Ditto and fused via an affine layer. The HoloLens 2 served as a scanner, sequence controller, and visualizer, communicating with the server through ROS. The structure of the project is as follows:

![](/assets/img/Process_HoloLens.png){: .mx-auto.d-block :}

Ditto utilizes an encoder (PointNet++)  to create representative point features invariant to input rotations. These encoders are fed by the HoloLens. After these encoders, the resultant point features are then fused with an attention layer. The fused point features are decoded for mesh reconstruction, segmentation (Geometry Feature Decoder), and joint axis prediction (Motion Feature Decoder). Then, they construct feature grid/planes by projecting and pooling the point features and query local features from the constructed feature grid/planes. Conditioning on local features, they use different decoders to predict occupancy, segmentation, and joint parameters with respect to the query points. From the final decoders we can obtain a mesh reconstruction, part segmentations into mobile and static parts, and a joint prediction.


![](/assets/img/Ditto_Arch.png){: .mx-auto.d-block :}


These results are sent to the HoloLens for human correction of the joint axis prediction, this is performed using HoloLens interactive features as can be seen in the following figure:

![](/assets/img/Human_interaction.png){: .mx-auto.d-block :}

Finally, after the user double checks the resultant joint axis, the final results are sent back to the server so we can take the final position and orientation of the joint axis to create the URDF model of the object. The following example represents a URDF model of my computer created with this model:


![](/assets/img/URDF_GIF.gif){: .mx-auto.d-block :}


This process is fast and easy to use for maping of articulated objects for later use in physics simulations.
The complete code for this project can be found [here](https://github.com/DiegoMachain/ArticulatedObjectMapping/tree/main).