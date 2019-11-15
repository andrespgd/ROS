

1-create file 01-myfirst.urdf
```
<?xml version="1.0"?>
<robot name="myfirst">
  <link name="base_link">
    <visual>
      <geometry>
        <cylinder length="0.6" radius="0.2"/>
      </geometry>
    </visual>
  </link>
</robot>
```

2-create file 01-myfirst.urdf
```
<launch>
       <arg name="model" />
       <arg name="gui" default="False" />
       <param name="robot_description" textfile="$(arg model)" />
       <param name="use_gui" value="$(arg gui)"/>
       <node name="joint_state_publisher" pkg="joint_state_publisher" type="joint_state_publisher"></node>
       <node name="robot_state_publisher" pkg="robot_state_publisher" type="state_publisher" />
       <node name="rviz" pkg="rviz" type="rviz" args="-d $(find urdf_tutorial)/urdf.rviz" />
</launch>
```

3-source
```
source /opt/ros/melodic/setup.bash
```

4-launch RVIZ
```
roslaunch urdf_tutorial model:=01-myfirst.urdf
```
