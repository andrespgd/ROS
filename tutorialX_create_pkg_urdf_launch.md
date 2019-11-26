From:

https://www.theconstructsim.com/ros-qa-142-how-to-create-launch-file-for-urdf-and-open-in-gazebo/

work in progress -> finish

```
~$ mkdir -p catkin_ws/src
~$ cd catkin_ws/src/
~/catkin_ws/src$ catkin_create_pkg my_robot_urdf rospy
~/catkin_ws/src$ ll
~/catkin_ws/src$ cd my_robot_urdf/
~/catkin_ws/src/my_robot_urdf$ ll
~/catkin_ws/src/my_robot_urdf$ mkdir urdf
~/catkin_ws/src/my_robot_urdf$ cd urdf
~/catkin_ws/src/my_robot_urdf/urdf$ gedit m2wr.urdf
~/catkin_ws/src/my_robot_urdf/urdf$ cd ..
~/catkin_ws/src/my_robot_urdf$ cd ..
~/catkin_ws/src$ ll
~/catkin_ws/src$ cd ..
~/catkin_ws$ mkdir launch
~/catkin_ws$ gedit spawn_urdf.launch
~/catkin_ws$ mv spawn_urdf.launch launch/
~/catkin_ws$ catkin_make
~/catkin_ws$ source devel/setup.bash 
~/catkin_ws$ roslaunch my_robot_urdf spawn_urdf.launch
```
NOTE: error when trying to roslaunch -> needs package.xml
