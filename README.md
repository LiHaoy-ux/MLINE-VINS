# MLINE-VINS

## MLINE-VINS: Robust Monocular Visual-Inertial SLAM With Flow Manhattan and Line Features

MLINE-VINS is a novel monocular visual-inertial odometry (VIO) system that leverages line features and Manhattan Word (MW) assumption. Our work primarily focuses on improving the speed of  line features and Manhattan frames matching, and uses MW to enhance the system performance.

## 1. Prerequisites

1.1 **Ubuntu** and **ROS**

Ubuntu  18.04.

ROS Melodic.

1.2. **Ceres Solver**
Follow [Ceres Installation](http://ceres-solver.org/installation.html), use **version 2.1.0** 

1.3 **OpenCV**

With **opencv_contrib**, use **version 3.14.5** requires library functions for EDLines

## 2. Build

Clone the repository and catkin_make:

```
    cd ~/catkin_ws/src
    git clone https://github.com/LiHaoy-ux/MLINE-VINS.git
    cd ../
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```

## 3. Run on the dataset

[EuRoC](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets)

```
roslaunch lfvins_estimator euroc.launch
rosbag play your_euroc_path/MH_01_easy.bag
```

[KAIST VIO](https://github.com/url-kaist/kaistviodataset)

```
roslaunch lfvins_estimator kaistvio.launch
rosbag play your_kasitvio_path/circle.bag
```

## 4.Deployed on your device

You should provide both IMU and camera ROS topics for the system.

Camera topic name, imu topic name, camera internal parameters, camera-imu extrinsic parameters, and IMU internal parameters need to be updated in the config.yaml before starting the system.

``` shell
*launch your sensor_ros_package*

*change your robot parameters*
cd ~/catkin_ws/src
gedit ../config/YOU_DEFINED_NAME.yaml

*launch EPLF-VINS*
source devel/setup.bash
roslaunch lfvins_estimator YOU_DEFINED_NAME.launch
```

## 5.Acknowledgements

Thanks to the open sources of  [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono), [PL-VINS](https://github.com/cnqiangfu/PL-VINS) and [EPLF-VINS](https://github.com/LeiXu1999/EPLF-VINS.git)

### The reference:

VINS-Mono:

``` shell
@ARTICLE{VINS-Mono,
	author={Qin, Tong and Li, Peiliang and Shen, Shaojie},
	journal={IEEE Trans. Robot.}, 
	title={{VINS-Mono: A Robust and Versatile Monocular Visual-Inertial State Estimator}}, 
	year={2018},
	volume={34},
	number={4},
	pages={1004-1020},
	doi={10.1109/TRO.2018.2853729}}
```

PL-VINS:

``` shell
@article{PL-VINS,
	author    = {Qiang Fu and Jialong Wang and Hongshan Yu and Islam Ali and Feng Guo and Hong Zhang},
	title     = {{PL-VINS: Real-Time Monocular Visual-Inertial SLAM with Point and Line}},
	journal   = {CoRR},
	volume    = {abs/2009.07462},
	year      = {2020},
	url       = {https://arxiv.org/abs/2009.07462},
	eprinttype = {arXiv},
	eprint    = {2009.07462},
	timestamp = {Wed, 09 Feb 2022 17:07:27 +0100},
	biburl    = {https://dblp.org/rec/journals/corr/abs-2009-07462.bib},
	bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

EPLF-VINS

```
@article{9998999,
  author   = {Xu, Lei and Yin, Hesheng and Shi, Tong and Jiang, Di and Huang, Bo},
  journal  = {IEEE Robotics and Automation Letters},
  title    = {EPLF-VINS: Real-Time Monocular Visual-Inertial SLAM With Efficient Point-Line Flow Features},
  year     = {2023},
  volume   = {8},
  number   = {2},
  pages    = {752-759},
  keywords = {Feature extraction;Simultaneous localization and mapping;Feature detection;Real-time systems;Optical flow;Location awareness;Optimization;Simultaneous localization and mapping (SLAM);line segment extraction and matching;monocular visual-inertial SLAM;localization},
  doi      = {10.1109/LRA.2022.3231983}
}
```

## 6.License

The source code is released under GPLv3 license.
We are still working on improving the code reliability. 
