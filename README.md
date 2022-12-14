# SLAM Map Building with TurtleBot
SLAM (Simultaneous Localization and Mapping) is a technique to estimate current location and draw a map. This can be done using TurtleBot which is a ROS standard platform robot that can run SLAM algorithms to build a map and can be controlled remotely.

Before you start, Make sure you did the following:
* Download and Install Ubuntu on PC
* Install ROS

These instruction was tested on Linux with Ubuntu 20.04 and ROS1 Noetic
# 1- Getting Started
## Install Dependent ROS Packages
```sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
```
## Install TurtleBot3 Packages
``` 
sudo apt install ros-noetic-dynamixel-sdk
```
``` 
sudo apt install ros-noetic-turtlebot3-msgs
```
``` 
sudo apt install ros-noetic-turtlebot3
```
# 2- Simulation
## Install Simulation Package
```
cd ~/catkin_ws/src/
```
```
git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
```
```
cd ~/catkin_ws && catkin_make
```
# 3- SLAM Simulation
## Launch Simulation World
Open a new terminal and simulation World, there are 3 versions of the TurtleBot model, I used waffle model

You can select one of these models ```burger```, ```waffle```, ```waffle_pi``` for the TURTLEBOT3_MODEL parameter
```
export TURTLEBOT3_MODEL=waffle
```
```
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
## Run SLAM Node
Open a new terminal and run the SLAM node, Gmapping SLAM method is used by default
```
export TURTLEBOT3_MODEL=waffle
```
```
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
## Run Teleoperation Node
In order to teleoperate the TurtleBot3 with the keyboard, launch the teleoperation node with below command in a new terminal window
```
export TURTLEBOT3_MODEL=waffle
```
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
## Save Map
When the map is created successfully, open a new terminal and save the map
```
rosrun map_server map_saver -f ~/map
```
# 4- Results
![Result](SLAM_Result.png)








