# Base Ubuntu 24.04 + ROS 2 Jazzy Image (CPU Only)
FROM osrf/ros:jazzy-desktop

# The base image already has a default user 'ubuntu' with UID 1000.
ARG USERNAME=ubuntu

# Set up sudo and user permissions, and basic tools
RUN apt-get update \
    && apt-get install -y sudo git curl nano wget \
    ros-jazzy-navigation2 ros-jazzy-nav2-bringup ros-jazzy-slam-toolbox \
    ros-jazzy-ros-gz-sim ros-jazzy-ros-gz-bridge ros-jazzy-xacro \
    ros-jazzy-rmw-cyclonedds-cpp \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

USER $USERNAME
WORKDIR /home/$USERNAME/amr_ws

# Setup rosdep for the user
RUN rosdep update

# Source ROS 2 automatically
RUN echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
