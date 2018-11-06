# RPi
>install ROS Melodic (Debian): http://wiki.ros.org/melodic/Installation/Debian
    http://asukiaaa.blogspot.com/2018/06/raspberry-pi-raspbianstretchrosmelodic.html

>install QT: Rasbian default package

### Check version
**pi@rpi3Bplus:~ $ uname -a**

Linux rpi3Bplus 4.14.79-v7+ #1159 SMP Sun Nov 4 17:50:20 GMT 2018 armv7l GNU/Linux

**pi@rpi3Bplus:~ $ lsb_release -a**



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
Open “/etc/dphys–swapfile” using “sudo nano”, edit CONF_SWAPSIZE variable (change 100MB to 1024MB):
    ...
    # CONF_SWAPSIZE=100
    CONF_SWAPSIZE=1024
Now we need to activate new swap space:

    $ sudo /etc/init.d/dphys-swapfile stop
    $ sudo /etc/init.d/dphys-swapfile start
Note: After installing ROS, MUST change swap space from 1024 to 100.
  
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
    
    mkdir -p ~/catkin_ws/src
    cd catkin_ws/src
    catkin_init_workspace
    cd ~/catkin_ws/
    catkin_make
    source ~/catkin_ws/devel/setup.bash
    echo 'source ~/catkin_ws/devel/setup.bash' >> ~/.bashrc
    export | grep ROS

