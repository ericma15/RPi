# RPi
>install ROS: https://www.intorobotics.com/how-to-install-ros-kinetic-on-raspberry-pi-3-running-raspbian-stretch-lite/
>install QT: Rasbian default package

### Install ROS melodic
  
    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
    wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
    sudo apt-get update
    sudo apt-get install -y python-rosdep python-rosinstall-generator python-wstool python-rosinstall build-essential cmake
    sudo apt install dirmngr
    sudo rosdep init
    rosdep update
    rosinstall_generator ros_comm --rosdistro melodic --deps --wet-only --tar > melodic-ros_comm-wet.rosinstall
    wstool init src melodic-ros_comm-wet.rosinstall
    rosdep install -y --from-paths src --ignore-src --rosdistro melodic -r --os=debian:stretch
    sudo ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release --install-space /opt/ros/melodic -j2
    source /opt/ros/melodic/setup.bash
    echo 'source /opt/ros/melodic/setup.bash' >> ~/.bashrc
    mkdir -p ~/catkin_workspace/src
    cd catkin_workspace/src
    catkin_init_workspace
    cd ~/catkin_workspace/
    catkin_make
    source ~/catkin_workspace/devel/setup.bash
    echo 'source ~/catkin_workspace/devel/setup.bash' >> ~/.bashrc
    export | grep ROS
  
### Install QT5.7

    sudo apt-get install qt5-default
    sudo apt-get install qtcreator
  
