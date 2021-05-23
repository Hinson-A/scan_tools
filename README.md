Laser scan tools for ROS
===================================

Overview
-----------------------------------

Laser scan processing tools. The meta-package contains:

* laser_ortho_projector: 将切斜的雷达数据投影到平面上．
* laser_scan_matcher: 基于pl-icp的扫描匹配的实现，并进行了位姿累加
*  laser_scan_matcher 功能包是增量激光扫描配准工具。该软件包允许扫描连续的 sensor_msgs / LaserScan 消息之间的匹配，
 并将估计的激光位置发布为 geometry_msgs / Pose2D 或 tf 变换。
 该包可以在没有其他传感器提供的任何测距估计的情况下使用。
 因此，它可以作为独立的里程计算器估算器
* laser_scan_sparsifier: 对雷达数据进行稀疏处理
* laser_scan_splitter: 将一帧雷达数据分段，并发布出去
* ncd_parser: 读取New College Dataset，转换成ros的scan 与 odometry 发布出去
* polar_scan_matcher: 基于Polar Scan Matcher的扫描匹配器的ros实现
* scan_to_cloud_converter: 将 sensor_msgs/LaserScan 数据转成 sensor_msgs/PointCloud2 的数据格式


 * `laser_ortho_projector`: calculates orthogonal projections of LaserScan messages
 
 * `laser_scan_matcher`: an incremental laser scan matcher, using Andrea Censi's Canonical 
Scan Matcher implementation. It downloads and installs Andrea Censi's Canonical Scan Matcher [1] locally.

 * `laser_scan_sparsifier`: takes in a LaserScan message and sparsifies it

 * `laser_scan_splitter`:  takes in a LaserScan message and splits 
it into a number of other LaserScan messages 

 * `ncd_parser`: reads in .alog data files from the New College Dataset [2]
and broadcasts scan and odometry messages to ROS.

 * `scan_to_cloud_converter`: converts LaserScan to PointCloud messages.

Installing
-----------------------------------

### Prerequisite

* ROS is installed
  * [1-liner ROS Indigo installation on Ubuntu](http://wiki.ros.org/ROS/Installation/TwoLineInstall)
* `apt-get install python-wstool`

### From binary (RECOMMENDED)

```
apt-get install ros-%ROS_DISTRO%-scan-tools

apt-get install ros-indigo-scan-tools        (Indigo)
```

### From source ###

Following is an example with ROS Indigo.

1. Create a [catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace) and navigate to its source directory (e.g. `~/catkin_ws/src`).

2. In your Catkin workspace, download source and build with the following commands.

```
cd ~/catkin_ws
wstool init src
wstool merge -t src https://raw.githubusercontent.com/ccny-ros-pkg/scan_tools/indigo/.rosinstall
rosdep install --from-paths src --ignore-src --rosdistro indigo -r -y
catkin_make                (or any build commands available in ROS, e.g. `catkin build`)
source devel/setup.bash
```

More info
-----------------------------------

http://wiki.ros.org/scan_tools

References
-----------------------------------
 [1] A. Censi, "An ICP variant using a point-to-line metric" Proceedings of the 
IEEE International Conference on Robotics and Automation (ICRA), 2008

 [2] M. Smith, I. Baldwin, W. Churchill, R. Paul, and P. Newman, 
The new college vision and laser data set, International Journal for Robotics 
Research (IJRR), vol. 28, no. 5, pp. 595599, May 2009.
 
