# Inherits from the CPU-only generic simulation image
FROM ghcr.io/robotics-avv/docker_files/jazzy_gazebo:latest

USER root

# Install simulation tools specific to your AMR (CPU only)
RUN apt-get update && apt-get install -y \
    python3-pip \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-xacro \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
