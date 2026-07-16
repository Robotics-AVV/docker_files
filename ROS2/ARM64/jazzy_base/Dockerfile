# Raspberry Pi ARM64 + ROS 2 Jazzy (Base only, no UI/Gazebo)
FROM osrf/ros:jazzy-ros-base

# Install basic tools and teleop packages
RUN apt-get update && apt-get install -y \
    python3-pip \
    git \
    nano \
    ros-jazzy-teleop-twist-keyboard \
    && rm -rf /var/lib/apt/lists/*

# The base image already has a default user 'ubuntu' with UID 1000.
ARG USERNAME=ubuntu

RUN apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

USER $USERNAME
WORKDIR /home/$USERNAME/amr_ws

# Setup rosdep for the user
RUN rosdep update

# Source ROS 2 automatically
RUN echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
