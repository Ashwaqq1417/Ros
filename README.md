# Ros
How to install ros in jesten-nano
Installation
Open a new terminal by pressing Ctrl + Alt + t or executing the “Terminal” application using the Ubuntu 18 launch system.

Set up the Jetson Nano to accept software from packages.ros.org:

$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
Add a new apt key:

$ sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
[Note: the ROS GPG key has changed due to a security issue on the ROS build farm server. If you configured your Jetson Nano for ROS following this guide before the 24th June 2019, please follow this guide to replace the old key in the correct way]

Update the Debian packages index:

$ sudo apt update
Install the ROS Desktop package, including support for rqt, rvizand other useful robotics packages:

$ sudo apt install ros-melodic-desktop
Note: “ROS Desktop Full” is a more complete package, however, it is not recommended for an embedded platform; 2D/3D simulators will be installed with it and they take too much space on ROM, and are too computationally hungry to be used on the Nano.

It is recommended to load the ROS environment variables automatically when you execute a new shell session. Update your .bashrc script:

$ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc 
$ source ~/.bashrc
Install and initialize rosdep. rosdep enables you to easily install system dependencies for source code you want to compile and is required to run some core components in ROS:

$ sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
$ sudo rosdep init 
$ rosdep update
Now the Jetson Nano is ready to execute ROS packages and become the brain of your autonomous robot.
