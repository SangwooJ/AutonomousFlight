
# AutonomousFlight
Deep Reinforcement Based Autonomous Flight

# Features
- Utilized the latest versions of Gazebo (Ignition) Simulator (Gazebo Garden), PX4 (v1.14) on Ubuntu 22.04
- Support ROS2(Humble) based PX4 offboard control
- Implemented advanced Deep Reinforcement Learning (DRL) for local navigation


# Setup 

## PX4 setup
Use the ubuntu.sh script in PX4 repo will install PX4&Gazebo Garden on Ubuntu 22.04. 
[https://docs.px4.io/main/en/dev_setup/dev_env_linux_ubuntu.html](https://docs.px4.io/main/en/dev_setup/dev_env_linux_ubuntu.html)

## ROS2 
Install ROS2 Humble.
[https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)

Source in the bash shell
```
source /opt/ros/humble/setup.bash
```
### Gazebo - ROS2 Configuration

Check the "Using a specific and unsupported Gazebo version with ROS 2" in the following link [https://gazebosim.org/docs/garden/ros_installation](https://gazebosim.org/docs/garden/ros_installation)
-> some command should be modified follow the instrutions below. 

- Installing rosdep rules to resolve Gazebo Garden libraries
```
sudo bash -c 'wget https://raw.githubusercontent.com/osrf/osrf-rosdep/master/gz/00-gazebo.list -O /etc/ros/rosdep/sources.list.d/00-gazebo.list'
rosdep update
<!-- check that resolve works --> 
rosdep resolve gz-garden
```
- Installing (ros_gz packages)[https://github.com/gazebosim/ros_gz/tree/humble] which includes ros_gz_bridge

  Create a colcon workspace:
  ```
  export GZ_VERSION=garden
  <!-- Setup the workspace -->
  mkdir -p ~/ws/src
  cd ~/ws/src
  ```
  Install dependencies (this may also install Gazebo):
  ```
  cd ~/ws
  rosdep install -r --from-paths src -i -y --rosdistro humble
  ```
  Build the workspace:
  ```
  <!-- Source ROS distro's setup.bash -->
  source /opt/ros/humble/setup.bash

  <!-- Build and install into workspace -->
  cd ~/ws
  colcon build

  <!-- Download needed software -->
  git clone https://github.com/gazebosim/ros_gz.git -b humble
  ```


# Progress

## Gazebo Environment 

```
make px4_sitl gz_x500
```
<img src="img/img1.png" width="300" height="300">

- Implemented Lidar sensor
<img src="img/lidar_screenshot.png" width="300" height="300">


