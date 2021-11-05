---
layout: post
title: Multi-Resolution Frontier-Based Planner
subtitle: The exploration algorithm for an autonomous exploration and mapping of the unknown environment.
categories: approach
tags: [github, approach]
---

Proposed multi-resolution frontier-based planner is a real-time capable exploration planner. The planner consists of the algorithm for detecting frontier points, followed by clustering of frontier points and selecting the best frontier point to be explored. Performance is achieved by not relying on data obtained directly from the 3D sensor, but on data obtained by a mapping algorithm. In order to cluster the frontier points, the properties of the Octree environment representation are used, which allows easy analysis with different resolutions.

![](https://www.youtube.com/watch?v=jiDi1lSX7EQ)

The repository for the implemented frontier-based strategy is available on [github](https://github.com/larics/uav_frontier_exploration_3d). If you use this code in a scholarly work, please cite our [journal paper](https://ieeexplore.ieee.org/document/9387089):

> **A Multi-Resolution Frontier-Based Planner for Autonomous 3D Exploration** \
> Ana Batinovic, Tamara Petrovic, Antun Ivanovic, Frano Petric and Stjepan Bogdan (IEEE Robotics and Automation Letters 2021)\


> @ARTICLE{Batinovic-RAL-2021,
  author={Batinovic, Ana and Petrovic, Tamara and Ivanovic, Antun and Petric, Frano and Bogdan, Stjepan},
  journal={IEEE Robotics and Automation Letters}, 
  title={A Multi-Resolution Frontier-Based Planner for Autonomous 3D Exploration}, 
  year={2021},
  volume={6},
  number={3},
  pages={4528-4535},
  doi={10.1109/LRA.2021.3068923}}


The frontier-based exploration planner is capable of autonomously exploring a previously unknown area, creating an occupancy grid map using Cartographer SLAM and generating an OctoMap. The planner does not require any prior knowledge of the environment, except for boundaries of the area to be explored. The planner may be applied to both indoor and outdoor environments.

It ensures frontiers detection, clustering and selection of the best frontier (a new target point). In each iteration, map and OctoMap are updated. Frontiers are clustered and a new target point is selected only when the prevoius target is reached. A robust frontier detection speeds up the exploration process, while a clustering algorithm ensures target evaluation in the real time.

The best frontier point to be visited is determined by estimating the benefit of the information gathered by visiting a candidate frontier point. The exploration loop is closed with an autonomous navigation to the selected frontier point, using the map generated through the exploration for trajectory planning and localization. Furthermore, the planner maintains a occupancy map of the environment. This guarantees that paths are only planned within free space, while giving a notion on exploration progress.


## Installation Instructions

### Prerequisites
* This package is tested on [Ubuntu 18.04](http://old-releases.ubuntu.com/releases/18.04.3/), it is assumed you have it installed.
* This package requires the installation of [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu) (tested). Refer to the [ROS tutorials](http://wiki.ros.org/ROS/Tutorials) for further information. 

### Installation

Detailed installation instructions to close the loop with the frontier-based exploration planner includes:
*  **Gazebo simulation of Ardupilot/PX4 UAV platform**
*  **Cartographer SLAM**
*  **Path planning and navigation**
*  **Frontier-based exploration planner**

Please refer to [Installation Instructions on Github Wiki](https://github.com/larics/uav_frontier_exploration_3d/wiki/Installation-Instructions) to install Gazebo simulation of Ardupilot/PX4 UAV platform, Cartographer SLAM, path planning and navigation module and frontier-based exploration planner.

## Exploration in progress 
During an unknown area exploration, the frontier-based planner publishes data on a number of topics. The ROS package RViz is used in order to visualize map, voxels (free and occupied) and paths.

Frontier points are marked red, candidates (clustered points) are yellow while the best frontier voxel is marked pink. The UAV planned a path (green) to the best frontier voxel (target point). OctoMap of the environment is updated in each iteration.

The house environment in both Gazebo simulator and RViz:

<p><img src="/assets/images/approach_1/house_exp1.png" alt="" /></p>
<p><img src="/assets/images/approach_1/house_exp2.png" alt="" /></p>
<p><img src="/assets/images/approach_1/house_exp3.png" alt="" /></p>
<p><img src="/assets/images/approach_1/house_exp4.png" alt="" /></p>
<p><img src="/assets/images/approach_1/house_exp5.png" alt="" /></p>
<p><img src="/assets/images/approach_1/house_octomap.png" alt="" /></p>




## Results



## Credits

The exploration algorithm was developed by [Ana Batinovic](mailto:ana.batinovic@fer.hr) with the help and support of the members of the [LARICS](https://larics.fer.hr/).