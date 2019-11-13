# ROS INSTALL
</br>

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

</br>

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


</br>

## ROS2-Kinetic for Ubuntu16.04
https://index.ros.org/doc/ros2/Installation/Dashing/Linux-Install-Debians/
```
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

sudo apt update && sudo apt install curl gnupg2 lsb-release

curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

sudo sh -c 'echo "deb [arch=amd64,arm64] http://packages.ros.org/ros2/ubuntu `lsb_release -cs` main" > /etc/apt/sources.list.d/ros2-latest.list'

sudo apt update

sudo apt install ros-dashing-desktop
```



</br></br>

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
