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
</br></br>


## ROS2-Dashing for Ubuntu18.04
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

sudo apt install python3-argcomplete
```
```
source /opt/ros/dashing/setup.bash
```
</br></br>


## ROS2-ELOQUENT for Ubuntu18.04
https://index.ros.org/doc/ros2/Installation/Eloquent/Linux-Install-Debians/
```
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

sudo apt update && sudo apt install curl gnupg2 lsb-release
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64,arm64] http://packages.ros.org/ros2/ubuntu `lsb_release -cs` main" > /etc/apt/sources.list.d/ros2-latest.list'
sudo apt update

sudo apt install ros-eloquent-desktop
sudo apt install ros-eloquent-ros-base

source /opt/ros/eloquent/setup.bash
sudo apt install python3-argcomplete
```

## ROS2 - prebuilt examples to test

term1
```
source /opt/ros/eloquent/setup.bash
ros2 run demo_nodes_cpp talker
```

term2
```
source /opt/ros/eloquent/setup.bash
ros2 run demo_nodes_py listener
```
</br></br>


## ROS2 - COLCON 
- is an iteration on the ROS build tools catkin_make, catkin_make_isolated, catkin_tools and ament_tools
https://index.ros.org/doc/ros2/Tutorials/Colcon-Tutorial/
```
sudo apt install python3-colcon-common-extensions
```
Sample package to build in ROS2 using COLCON
```
source /opt/ros/dashing/setup.bash 
mkdir -p ~/ros2_example_ws/src
cd ~/ros2_example_ws
git clone https://github.com/ros2/examples src/examples
cd ~/ros2_example_ws/src/examples/
git checkout $ROS_DISTRO
cd ~/ros2_example_ws
colcon build --symlink-install
```
Source the environment:
```
. install/setup.bash
```
terminal1 - subscriber
```
cd ros2_example_ws/
. install/setup.bash 
ros2 run examples_rclcpp_minimal_subscriber subscriber_member_function
```
terminal2 - publisher
```
cd ros2_example_ws/
. install/setup.bash 
ros2 run examples_rclcpp_minimal_publisher publisher_member_function
```
</br></br>

## ROS2 - Create your own packages
```
ros2 pkg create ros2_example2_ws
```
-will create files: CMakeLists.txt, package.xml
-will create folders: include , src

</br></br>

## ROS2 - ELOQUENT - Create Python packages
https://www.youtube.com/watch?v=94J0Wl_8JKQ
https://index.ros.org/doc/ros2/Tutorials/Writing-A-Simple-Py-Publisher-And-Subscriber/
```
mkdir -p ros2_ws/src
cd ros2_ws/src/

# create a c++ package
ros2 pkg create --build-type ament_cmake test_ros2_pkg
# remove it
rm -fr test_ros2_pkg

# create a Python package using AMENT_PYTHON (w/ dependencies rclpy std_msgs)
ros2 pkg create --build-type ament_python ros2_pypkg --dependencies rclpy std_msgs
```
</br></br>

## Cool ROS samples

-- Robotic arm simulation for Ubuntu16-ROS1-Melodic (Does NOT in Ubuntu18-ROS1-Melodic!!!) (NOT ROS2!!!)
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

-- Wheeled robot simulation for Ubuntu16-ROS1-Melodic (Does NOT in Ubuntu18-ROS1-Melodic!!!) (NOT ROS2!!!)
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

-- Full environment simulation for Ubuntu18-ROS1-Melodic (NOT ROS2!!!)
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


-- Good post on how ROS and Gazebo communicate

https://newscrewdriver.com/2018/09/08/examining-basic-requirements-for-mapping-in-ros/


-- Online URDF 3D viewer

https://mymodelrobot.appspot.com/


-- ROS Tutorial - look at Wiki Chapters

https://github.com/Lauro199471/ROS_Tutorial/wiki


-- Basic concepts on ROS and Gazebo

https://www.generationrobots.com/blog/en/robotic-simulation-scenarios-with-gazebo-and-ros/


- Good car example to follow

https://github.com/stevendaniluk/ghost


- Good simple ROS tutorial with useful commands

http://www.daslhub.org/unlv/wiki/lib/exe/fetch.php?media=courses:ros:ros_3v2.pptx



- Commands to check URDF:
```
>check_urdf
>urdf_to_graphviz
+visual link
```


- ROS command: convert .xacro to .urdf , check, create .PDF .GV, view .GV
```
source devel/setup.bash
rosrun xacro xacro rrbot.xacro > rrbot.urdf
check_urdf rrbot.urdf
urdf_to_graphiz rrbot.urdf
```
NOTE: how to view the .GV file ?????


- ROS command: if a master is running:
```
rqt_graph
```

