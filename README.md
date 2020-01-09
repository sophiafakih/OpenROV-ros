# OpenROV-ros
ROS implementation for the OpenROV / ROS integration project

This package is a fork of the package written by David Lane and Connor Brew. This was tested and built under ROS Kinetic & Ubuntu 16.04.

Installation guide:

Install ROS kinetic: http://wiki.ros.org/kinetic/Installation/Ubuntu

Creating a ROS workspace:

    mkdir -p ~/catkin_ws/src
    cd ~/catkin_ws/
    catkin_make

Install rosbridge:

    sudo apt-get install ros-kinetic-rosbridge-server
    sudo apt-get install ros-kinetic-rosbridge-suite
    source /opt/ros/kinetic/setup.bash
    
Install OpenROV-ros in your workspace:

    cd ~/catkin_ws/src
    git clone https://github.com/sophiafakih/OpenROV-ros.git openrov
    cd ~/catkin_ws/
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
    source ~/.bashrc
    

List of currently available commands to control the OpenROV:

#Run motors [port, vert, stbd]
    rostopic pub -1 openrov/motortarget openrov/motortarget '{motors:[1500, 1500, 1500]}'

#Lasser toggle
    rostopic pub -1 openrov/laser_toggle std_msgs/Int32 '{data: 0}'

#Light level control
    rostopic pub -1 openrov/light_command std_msgs/Float32 '{data: 0.5}'

#Cam servo control
    rostopic pub -1 openrov/servo_cam_tilt std_msgs/Float32 '{data: 0.0}' 

#Lift and yaw control
    rostopic pub /openrov/cmd\_rate geometry\_msgs/Twist '{linear: {x: 0.0, y: 0.0, z: 0.5}, angular: {x: 0.0,y: 0.0,z: 0.5}}'
