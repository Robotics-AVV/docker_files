# Inherits from your CUDA base image
FROM your_registry/jazzy_base_cuda:latest

USER root

# Install Gazebo Harmonic on top of the CUDA base
RUN apt-get update && apt-get install -y \
    ros-jazzy-ros-gz \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
