FROM ros:jazzy-ros-base

# The base image already has a default user 'ubuntu' with UID 1000.
ARG USERNAME=ubuntu

# Install basic tools, MAVROS, and V-SLAM dependencies
RUN apt-get update \
    && apt-get install -y sudo git curl nano wget \
    python3-pip python3-colcon-common-extensions build-essential \
    ros-jazzy-mavros ros-jazzy-mavros-extras ros-jazzy-mavros-msgs \
    ros-jazzy-rtabmap-ros ros-jazzy-image-transport-plugins \
    ros-jazzy-rmw-cyclonedds-cpp \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

# Install MAVLink geographic datasets (Required for MAVROS)
# Running as root before switching user
RUN wget -O /tmp/install_geographiclib_datasets.sh https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh \
    && bash /tmp/install_geographiclib_datasets.sh

# Switch to the non-root user
USER $USERNAME
WORKDIR /home/$USERNAME/drone_ws

# Setup rosdep for the user
RUN rosdep update

# Source ROS 2 and set CycloneDDS as the default middleware (often better for Raspberry Pi / Wifi)
RUN echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
RUN echo "export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp" >> ~/.bashrc
RUN echo "if [ -f /home/$USERNAME/drone_ws/install/setup.bash ]; then source /home/$USERNAME/drone_ws/install/setup.bash; fi" >> ~/.bashrc

CMD ["bash"]
