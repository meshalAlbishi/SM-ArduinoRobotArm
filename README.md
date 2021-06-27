# SM-ArduinoRobotArm
The purpose of this task is to setup the ROS on ubuntu and install the arms packages.

## Requirements  
- VirtualBox, available to download from [here](https://www.virtualbox.org/wiki/Downloads).
- Ubuntu 16.04, available to download from [here](https://releases.ubuntu.com/16.04/).

## Setup

After complete setup the VirtualBox and Ubuntu:
navigate to the terminal, and write the following command

### Setup ROS
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

sudo apt-get update

sudo apt-get install ros-kinetic-desktop-full

apt-cache search ros-kinetic

echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

sudo apt install python-rosdep

sudo rosdep init

rosdep update

sudo apt-get install ros-noetic-catkin

mkdir -p ~/catkin_ws/src

cd ~/catkin_ws/

catkin_make

cd ~/catkin_ws/src
```

After setup the ROS and it ready, now we will setup the arm packages
### Setup Arm Package
the first step, to clone the arm repositories ```git clone https://github.com/smart-methods/arduino_robot_arm.git ```

now we need to complete the following packages
```
cd ~/catkin_ws

rosdep install --from-paths src --ignore-src -r -y

sudo apt-get install ros-kinetic-moveit

sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui

sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher

sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control

sudo nano ~/.bashrc
```
after the last step, it will open a file (.bashrc), at the end of the file add the follwing line

(source /home/PC_NAME/catkin_ws/devel/setup.bash), replcae PC_NAME with yours

then ```ctrl + o```

now you need to launch it

```
source ~/.bashrc
roslaunch robot_arm_pkg check_motors.launch
```

## Result
video of the result available [here](https://github.com/meshalAlbishi/SM-ROS-ArduinoRobotArm/blob/main/arm.mp4).
