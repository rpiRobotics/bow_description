# bow_description
This ROS package provides urdf description files for baxter on ridgeback mobile base. 

1. Download ros packages needed for Ridgeback mobile base using:
sudo apt-get install ros-indigo-ridgeback-msgs ros-indigo-ridgeback-navigation ros-indigo-ridgeback-control ros-indigo-ridgeback-description ros-indigo-ridgeback-lms1xx

2. Download ridgeback_gazebo from github:
https://github.com/ridgeback/ridgeback_simulator/tree/indigo-devel/ridgeback_gazebo

3. Follow workstation setup for Baxter SDK installation:
http://sdk.rethinkrobotics.com/wiki/Workstation_Setup

4. Install baxter simulator by following steps given on:
http://sdk.rethinkrobotics.com/wiki/Simulator_Installation

5. cd to the ros workspace directory and catkin_make packages.

6. source devel/setup.bash

If you want to visualize the Baxter on Ridgeback in gazebo:

1. download bow_gazebo package:
https://github.com/rpiRobotics/bow_gazebo

2. catkin_make in ros workspace directory

3. source devel/setup.bash

4. roslaunch bow_gazebo bow_world.launch

5. Write to topic /cmd_vel to control mobile base.

Since the implementation of ridgeback simulator is incomplete, the mobile base might not function properly.

Some useful commands:

1. To convert xacro to urdf format:
rosrun xacro xacro.py -o bow.urdf bow.urdf.xacro

2. To check correctness of urdf file:
check_urdf bow.urdf

3. To get link graph of robot urdf:
urdf_to_graphiz bow.urdf

4. To visualize robot model in rviz:
roslaunch urdf_tutorial display.launch model:=bow.urdf gui:=True

5. To launch empty gazebo world:
roslaunch gazebo_ros empty_world.launch

6. To spawn robot model on gazebo at x y z location:
rosrun gazebo_ros spawn_model -file bow.urdf -urdf -x 0 -y 0 -z 0.1 -model bow
