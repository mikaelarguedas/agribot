FROM ros:noetic

RUN apt-get -qq update && apt-get upgrade -y
RUN apt-get install -y git micro python3-catkin-tools python3-osrf-pycommon
ENV AGRI_WS $HOME/agribot_ws
RUN mkdir -p $AGRI_WS/src
WORKDIR $AGRI_WS/src
RUN git clone https://github.com/mikaelarguedas/agribot.git -b noetic_and_docker

WORKDIR $AGRI_WS
RUN rosdep update --rosdistro $ROS_DISTRO \
    && rosdep install -y --from-paths src --ignore-src
RUN catkin config --extend /opt/ros/$ROS_DISTRO
RUN catkin build

CMD ["bash"]
