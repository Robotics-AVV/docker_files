# Inherits from the CPU-only generic base image
FROM your_registry/jazzy_base:latest

USER root

# Install tools specific to your AMR (CPU only)
RUN apt-get update && apt-get install -y \
    python3-pip \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-xacro \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
