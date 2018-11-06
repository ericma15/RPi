# RPi
>install ROS: https://www.intorobotics.com/how-to-install-ros-kinetic-on-raspberry-pi-3-running-raspbian-stretch-lite/

>install QT: Rasbian default package

### Check version
**pi@rpi3Bplus:~ $ uname -a**

Linux rpi3Bplus 4.14.79-v7+ #1159 SMP Sun Nov 4 17:50:20 GMT 2018 armv7l GNU/Linux

### Install QT5.7
    sudo apt-get install qt5-default
    sudo apt-get install qtcreator
  
#### Qt Tool Chain Settings
  go to Tools -> Options..-> Build & Run -> Compilers tab. click in "Add -> GCC". 
  On "Compiler Path" set to "/home/<you>/opt/gcc-4.7-linaro-rpi-gnueabihf/bin/arm-linux-gnueabihf-g+". 
  Name it "ARM GCC" or similar. 

#### Qt Version settings.
  go to Tools -> Options..-> Build & Run -> Qt Versions tab. 
  Click in "Add.." and choose you qmake for raspberry "/usr/local/qt5pi/bin/qmake".


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

