# RPi
>install ROS Melodic (Debian): http://wiki.ros.org/melodic/Installation/Debian
    http://asukiaaa.blogspot.com/2018/06/raspberry-pi-raspbianstretchrosmelodic.html

>install QT: https://github.com/tranter/raspberry-pi-qt-builds

### Change RPi's swapfile size

$ sudo nano etc/dphys–swapfile; edit CONF_SWAPSIZE variable (change 100MB to 1024MB):
    
    ...
    # CONF_SWAPSIZE=100
    CONF_SWAPSIZE=1024
    
Restart new swap space and check memory:

    $ sudo /etc/init.d/dphys-swapfile stop
    $ sudo /etc/init.d/dphys-swapfile start
    $ free -m
    pi@raspberrypi:~ $ free -m
                  total        used        free      shared  buff/cache   available
    Mem:            927         228         269          34         429         643
    Swap:          1023           0        1023
    

### Check version
**pi@rpi3Bplus:~ $ uname -a**

    Linux rpi3Bplus 4.14.79-v7+ #1159 SMP Sun Nov 4 17:50:20 GMT 2018 armv7l GNU/Linux

**pi@rpi3Bplus:~ $ lsb_release -a**

    Distributor ID:	Raspbian
    Description:	Raspbian GNU/Linux 9.4 (stretch)
    Release:	9.4
    Codename:	stretch

### Install QT5 required packages
autotools-dev bison build-essential default-libmysqlclient-dev dpkg-dev firebird-dev flex freetds-dev 
gstreamer1.0-alsa gstreamer1.0-libav gstreamer1.0-omx gstreamer1.0-omx-rpi gstreamer1.0-omx-rpi-config gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x icu-devtools libasound2-dev libatk1.0-dev libatk-bridge2.0-dev libassimp-dev libatspi2.0-dev libaudit-dev libavcodec-dev libavformat-dev 
libbison-dev libbsd-dev libc6-dev libcairo2-dev libcap-ng-dev libbluetooth-dev libc-dev-bin libcups2-dev libcupsimage2-dev libclang-dev libdbus-1-dev libdevmapper-dev libdmx-dev libdouble-conversion-dev libdrm-dev libegl1-mesa-dev libepoxy-dev libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libgbm-dev libgcc-6-dev libgcrypt20-dev libgdk-pixbuf2.0-dev libgl1-mesa-dev libgles2-mesa-dev libglib2.0-dev libglu1-mesa-dev libgmp-dev libgpg-error-dev libgraphite2-dev 
libgstreamer1.0 libgstreamer1.0-0 libgstreamer1.0-dev libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-base1.0-dev libgtk-3-dev libharfbuzz-dev libhunspell-dev libice-dev libicu-dev libinput-dev libjbig-dev libjpeg62-turbo-dev libjpeg-dev libltdl-dev liblzma-dev libmariadbclient-dev libmariadbclient-dev-compat libmnl-dev libmtdev-dev libpango1.0-dev libpciaccess-dev libpcre3-dev libpipeline-dev libpixman-1-dev libpng-dev libpq-dev libproxy-dev libpthread-stubs0-dev libpulse-dev
libpython2.7-dev libpython3.5-dev libpython3-dev libpython-all-dev libpython-dev libqt5opengl5-dev libqt5webkit5-dev libraspberrypi-dev librtimulib-dev libselinux1-dev libsepol1-dev libsgutils2-dev libsm-dev libsqlite3-dev libssl1.0-dev libstdc++-6-dev libswscale-dev libsystemd-dev libtiff5-dev libudev-dev libwayland-dev 
libx11-dev libx11-xcb1 libx11-xcb-dev libxau-dev libxaw7-dev libxcb1 libxcb1-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-icccm4 libxcb-icccm4-dev libxcb-image0 libxcb-image0-dev libxcb-keysyms1 libxcb-keysyms1-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-render-util0 libxcb-render-util0-dev libxcb-shape0-dev libxcb-shm0 libxcb-shm0-dev libxcb-sync0-dev libxcb-sync1 libxcb-sync-dev libxcb-util0-dev libxcb-xf86dri0-dev libxcb-xfixes0-dev libxcb-xinerama0 libxcb-xinerama0-dev libxcb-xkb-dev libxcb-xv0-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev libxi-dev libxinerama-dev libxkbcommon-dev libxkbcommon-x11-dev libxkbfile-dev libxml2-dev libxmu-dev libxmuu-dev libxpm-dev libxrandr-dev libxrender-dev libxres-dev libxshmfence-dev libxt-dev libxtst-dev libxv-dev libxxf86vm-dev linux-libc-dev manpages-dev mesa-common-dev 
nettle-dev python2.7-dev python3.5-dev python3-dev python3-smbus python-all-dev python-dev python-smbus 
qtbase5-dev qtbase5-dev-tools qtbase5-private-dev qtdeclarative5-dev qtdeclarative5-private-dev qttools5-dev-tools 
ruby unixodbc-dev x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-dmx-dev x11proto-dri2-dev x11proto-dri3-dev x11proto-fixes-dev x11proto-fonts-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-present-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev xutils-dev zlib1g-dev 

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

