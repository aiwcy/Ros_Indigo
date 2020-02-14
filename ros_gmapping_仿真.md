# 在gazebo中运行turtlebot机器人模拟gmapping的slam过程
[来自爱学习的草莓熊的CSDN](https://blog.csdn.net/lingchen2348/article/details/79503970 "来自爱学习的草莓熊")

## 1.安装完整版ROS

## 2.安装一些ROS-Gazebo组件

	sudo apt-get install ros-kinetic-gazebo-ros-pkgs ros-kinetic-gazebo-ros-control

## 3.下载Gazobo的模型包
完整安装ROS后自带的Gazebo没有相应的模型文件，启动empty_world.launch后可能出现黑屏，此时的gazebo里面啥模型也没有，必须下载相应的模型文件，并复制到~/.gazebo/models文件夹下，注意，这是一个隐藏文件夹。下载模型库的方法见另一位博主笔记：[《Gazebo问题修复 - CSDN博客》](https://blog.csdn.net/qq_39989653/article/details/78472097 "")，里面有稍微快一些的下载链接。

## 4.安装turtlebot相关包

	$ sudo apt-get install ros-kinetic-turtlebot-*

## 5.仿真演示
下面启动一个仿真程序来做个演示，这个示例程序也是ROS官网给出的示例，很多入门教程都是以此为基础。

### 5.1 启动Gazebo并加载机器人、环境模型

	roslaunch turtlebot_gazebo turtlebot_world.launch

![](.\data\img\gazebo.jpg)


### 5.2启动键盘遥控节点

	roslaunch turtlebot_teleop keyboard_teleop.launch --screen

![](.\data\img\keyboard.jpg)
此时，选中该命令窗口，按照提示，使用键盘上的u、i等键就可以看见机器人的Gazebo窗口中运动。

### 5.3运行gmapping

	roslaunch turtlebot_gazebo gmapping_demo.launch

### 5.4开启rviz观察建图过程

	roslaunch turtlebot_rviz_launchers view_navigation.launch

![](.\data\img\rviz.jpg)
这是用gmapping建图的过程

**问题1：**
在运行Gazebo的过程中遇到了报错，例如：*/opt/ros/indigo/share/gazebo_ros_pkgs/gazebo_ros/scripts/gazebo: 25: .: Can't open /share/gazebo//setup.sh*

**解决：**问题可能是找不到gazebo的启动脚本在哪里，将/opt/ros/indigo/share/gazebo_ros_pkgs/gazebo_ros/scripts/文件夹下面要启动确can't open 的脚本中的*setup_path=$(pkg-config --variable=prefix gazebo)/share/gazebo/*改为setup_path=/usr/share/gazebo

[解决方法网址](https://answers.ros.org/question/215796/problem-for-install-gazebo_ros_package/ "answers ros")

