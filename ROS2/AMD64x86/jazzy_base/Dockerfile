# Base Ubuntu 24.04 + ROS 2 Jazzy Image (CPU Only)
FROM osrf/ros:jazzy-desktop

# The base image already has a default user 'ubuntu' with UID 1000.
ARG USERNAME=ubuntu

# Set up sudo and user permissions, and basic tools
RUN apt-get update \
    && apt-get install -y sudo git curl nano wget \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

USER $USERNAME
WORKDIR /home/$USERNAME/amr_ws

# Setup rosdep for the user
RUN rosdep update

# Source ROS 2 automatically
RUN echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
