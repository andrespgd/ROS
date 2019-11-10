# ROS INSTALL
</br></br>

## ROS1-Melodic for Ubuntu18.04

http://wiki.ros.org/melodic/Installation/Ubuntu

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt update
sudo apt install ros-melodic-desktop-full
sudo rosdep init
rosdep update
```

bash env setup:
```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
OR
```
source /opt/ros/melodic/setup.bash
```

</br></br>

## ROS1-Kinetic for Ubuntu16.04
http://wiki.ros.org/kinetic/Installation/Ubuntu
```diff
- will NOT install on Ubuntu18.04 !!!
```
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt-get update
sudo apt-get install ros-kinetic-desktop-full
sudo rosdep init
rosdep update
sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential
```
```
source /opt/ros/kinetic/setup.bash
```


## Cool ROS samples

-- robotic arm simulation -- Does NOT in Ubuntu18-Ros1-Melodic!
```
source /opt/ros/melodic/setup.bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src 
git clone https://TheConstruct@bitbucket.org/theconstructcore/iri_wam.git -b kinetic
git clone https://github.com/ros-controls/ros_controllers
git clone https://github.com/ros-drivers/four_wheel_steering_msgs
git clone https://github.com/ros-controls/urdf_geometry_parser
cd ..
catkin_make
roslaunch iri_wam_gazebo main.launch
```

-- wheeled robot simulation -- Does NOT in Ubuntu18-Ros1-Melodic!
```
source /opt/ros/melodic/setup.bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src 
git clone https://TheConstruct@bitbucket.org/theconstructcore/summit_xl.git -b kinetic
git clone https://github.com/RobotnikAutomation/robotnik_msgs
git clone https://github.com/cra-ros-pkg/robot_localization
git clone https://github.com/ros-geographic-info/geographic_info
git clone https://github.com/ros-geographic-info/unique_identifier
git clone https://github.com/mavlink/mavros
git clone https://github.com/mavlink/mavlink
cd ..
catkin_make
roslaunch sumit_xl_course_basics main.launch
```

-- full environment simulation -- Works in Ubuntu18-Ros1-Melodic
```
source /opt/ros/melodic/setup.bash
mkdir -p ~/catkin_ws/src
cd catkin_ws/src
hg clone https://TheConstruct@bitbucket.org/osrf/servicesim
git clone https://github.com/Kukanani/vision_msgs
cd ..
catkin_make
roslaunch servicesim servicesim.launch
```
