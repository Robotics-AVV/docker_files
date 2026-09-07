# TurtleBot 4 offboard SLAM + Gazebo Harmonic simulation, with GPU passthrough.
#
# Inherits turtlebot4_base (which is itself FROM the CPU-only jazzy_base), so the
# two NVIDIA ENV lines from jazzy_base_cuda are repeated here rather than inherited
# — Docker has no multiple inheritance, and duplicating two ENV lines beats
# re-parenting turtlebot4_base or duplicating its whole apt install list under
# jazzy_gazebo_cuda.
FROM ghcr.io/robotics-avv/docker_files/turtlebot4_base:latest

# NVIDIA GPU settings for hardware acceleration (same as jazzy_base_cuda).
ENV NVIDIA_VISIBLE_DEVICES=all
ENV NVIDIA_DRIVER_CAPABILITIES=graphics,compute,utility

USER root

# ros-jazzy-turtlebot4-simulator pulls in turtlebot4_gz_bringup, turtlebot4_gz_gui_plugins,
# turtlebot4_gz_toolbox, and the irobot_create_gz_* chain (gz bringup/plugins/toolbox,
# irobot_create_nodes, irobot_create_common_bringup). Verified by building this image:
# irobot_create_gz_plugins itself depends on the ros-jazzy-ros-gz metapackage (and
# therefore ros_gz_sim_demos + image_transport_plugins come along for the ride) — there
# is no way to get the TB4/Create3 Gazebo bringup without it, so it is not installed
# explicitly here, just pulled in as a transitive dependency.
#
# ros-jazzy-laser-filters is the config-only /scan filtering layer shared by both sim
# and real hardware.
RUN apt-get update && apt-get install -y \
    ros-jazzy-turtlebot4-simulator \
    ros-jazzy-laser-filters \
    && rm -rf /var/lib/apt/lists/*

USER ubuntu
