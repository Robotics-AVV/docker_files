# Inherits from the CPU-only generic Jazzy base image
FROM ghcr.io/robotics-avv/docker_files/jazzy_base:latest

USER root

# TurtleBot 4 offboard packages: navigation (bundles slam_toolbox launch
# wrappers), description (robot model for RViz), msgs, and RViz configs/
# launch helpers. Plus teleop for driving during mapping.
RUN apt-get update && apt-get install -y \
    ros-jazzy-turtlebot4-navigation \
    ros-jazzy-turtlebot4-description \
    ros-jazzy-turtlebot4-msgs \
    ros-jazzy-turtlebot4-viz \
    ros-jazzy-irobot-create-msgs \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-teleop-twist-joy \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
