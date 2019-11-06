# ROS INSTALL

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

## ROS1-Kinetic for Ubuntu16.04
http://wiki.ros.org/kinetic/Installation/Ubuntu
```diff
- it will not install on Ubuntu18.04 !!!
- $ sudo apt-get install ros-kinetic-desktop-full
- E: Unable to locate package ros-kinetic-desktop-full
```
