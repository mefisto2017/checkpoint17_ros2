FROM osrf/ros:galactic-desktop

# Change to bash
SHELL ["/bin/bash", "-c"] 

# Minimal setup
RUN apt-get update \
    && apt-get install -y  apt-utils \
    locales \
    lsb-release
ARG DEBIAN_FRONTEND=noninteractive
RUN dpkg-reconfigure locales

# Install ROS dependencies
RUN apt-get install -y git \
    ros-galactic-joint-state-publisher \
    ros-galactic-robot-state-publisher \
    ros-galactic-cartographer \
    ros-galactic-cartographer-ros \
    ros-galactic-gazebo-plugins \
    ros-galactic-teleop-twist-keyboard \
    ros-galactic-teleop-twist-joy \
    ros-galactic-xacro \
    ros-galactic-nav2* \
    ros-galactic-urdf \
    ros-galactic-v4l2-camera
    

# Clone the tortoise repo
RUN mkdir -p /root/ros2_ws/src 
COPY ./tortoisebot/tortoisebot_gazebo/ /root/ros2_ws/src/tortoisebot_gazebo
COPY ./tortoisebot/tortoisebot_description/ /root/ros2_ws/src/tortoisebot_description
COPY ./tortoisebot/tortoisebot_bringup/ /root/ros2_ws/src/tortoisebot_bringup
COPY ./tortoisebot/ydlidar-ros2/ /root/ros2_ws/src/ydlidar
COPY ./tortoisebot/tortoisebot_navigation/ /root/ros2_ws/src/tortoisebot_navigation
COPY ./tortoisebot/tortoisebot_waypoints/ /root/ros2_ws/src/tortoisebot_waypoints

# Link python3 to python otherwise ROS scripts fail when using the OSRF contianer
RUN ln -s /usr/bin/python3 /usr/bin/python

# Navigate to the catkin workspace
WORKDIR /root/ros2_ws

RUN source /opt/ros/galactic/setup.bash \
    && colcon build

RUN echo source /opt/ros/ros2_ws/setup.bash >> /root/.bashrc
RUN echo source /root/ros2_ws/install/setup.bash >> /root/.bashrc

# Clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /root/.cache\
    && apt-get clean && apt autoclean