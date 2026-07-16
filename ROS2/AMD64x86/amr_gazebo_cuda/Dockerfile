# Inherits from the CUDA-enabled generic simulation image
FROM your_registry/jazzy_gazebo_cuda:latest

USER root

# Install simulation tools specific to your AMR that require GPU acceleration
RUN apt-get update && apt-get install -y \
    python3-pip \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-xacro \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
