## Followed tutorial from:

https://u.cs.biu.ac.il/~yehoshr1/89-685/ROS_Lecture9.pptx

## Single body

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


## Joint

1-create 02-multipleshapes.urdf
```
<?xml version="1.0"?>
<robot name="multipleshapes">
  <link name="base_link">
    <visual>
      <geometry>
        <cylinder length="0.6" radius="0.2"/>
      </geometry>
    </visual>
  </link>

  <link name="right_leg">
    <visual>
      <geometry>
        <box size="0.6 .2 .1"/>
      </geometry>
    </visual>
  </link>

  <joint name="base_to_right_leg" type="fixed">
    <parent link="base_link"/>
    <child link="right_leg"/>
  </joint>
</robot>
```

2-
```
roslaunch urdf_tutorial display.launch model:=02-mutipleshapes.urdf
```

## Joint with origin for both link and joint

1- create
```
<?xml version="1.0"?>
<robot name="origins">
  <link name="base_link">
    <visual>
      <geometry>
        <cylinder length="0.6" radius="0.2"/>
      </geometry>
    </visual>
  </link>
  <link name="right_leg">
    <visual>
      <geometry>
        <box size="0.6 .2 .1"/>
      </geometry>
      <origin rpy="0 1.57075 0" xyz="0 0 -0.3"/>
    </visual>
  </link>
  <joint name="base_to_right_leg" type="fixed">
    <parent link="base_link"/>
    <child link="right_leg"/>
    <origin xyz="0.22 0 .25"/>
  </joint>
</robot>
```

2-
```
roslaunch urdf_tutorial display.launch model:=03-origins.urdf
```




