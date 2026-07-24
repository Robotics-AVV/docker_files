# Inherits from your CPU-only Gazebo base image
FROM ghcr.io/robotics-avv/docker_files/jazzy_gazebo:latest

# Switch to root to install packages
USER root

# Install MAVROS and V-SLAM dependencies
RUN apt-get update && apt-get install -y \
    ros-jazzy-mavros ros-jazzy-mavros-extras ros-jazzy-mavros-msgs \
    ros-jazzy-rtabmap-ros ros-jazzy-image-transport-plugins \
    && rm -rf /var/lib/apt/lists/*

# Install MAVLink geographic datasets (Required for MAVROS)
RUN wget -O /tmp/install_geographiclib_datasets.sh https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh \
    && bash /tmp/install_geographiclib_datasets.sh

# Switch back to development user
USER ubuntu
