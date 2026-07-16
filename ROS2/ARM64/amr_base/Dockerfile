# Inherits from the generic ARM64 Jazzy base image
FROM your_registry/jazzy_base_arm64:latest

USER root

# Install tools specific to your AMR that run directly on the physical Raspberry Pi
RUN apt-get update && apt-get install -y \
    python3-pip \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-xacro \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
