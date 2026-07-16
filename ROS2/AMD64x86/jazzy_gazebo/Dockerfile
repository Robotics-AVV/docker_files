# Inherits from your CPU-only base image
FROM ghcr.io/robotics-avv/docker_files/jazzy_base:latest

# Switch to root to install packages
USER root

# Install Gazebo Harmonic
RUN apt-get update && apt-get install -y \
    ros-jazzy-ros-gz \
    && rm -rf /var/lib/apt/lists/*

# Switch back to development user
USER ubuntu
