# Inherits from the CUDA-enabled generic base image
FROM your_registry/jazzy_base_cuda:latest

USER root

# Install tools specific to your AMR that also need GPU (AI, vision, etc)
RUN apt-get update && apt-get install -y \
    python3-pip \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-xacro \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
