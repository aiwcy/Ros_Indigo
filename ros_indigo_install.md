# 安装ROS Indigo
根据网上资料，Ubuntu14.04适合安装Indigo版本，16.04适合安装Kinect版本

## 1.设置源
    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

## 2.设置key
    sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

## 3.安装
### 3.1确认Bebian安装包是最新的
	sudo apt-get update && sudo apt-get install dpkg

### 3.2安装
安装完全版

	sudo apt-get install ros-indigo-desktop-full
安装Desktop：ROS, rqt, rviz, and robot-generic libraries

	sudo apt-get install ros-indigo-desktop

## 4.初始化rosdep
在使用ROS前需要对rosdep初始化。rosdep让我们可以轻松为们想要编译的源代码安装系统依赖项，并且安装ROS运行中所需的核心组件

    sudo rosdep init
	rosdep update
注：[运行上面代码可能会报错，我是通过连接中的（1）删除已经存在的初始化文件解决的](https://www.cnblogs.com/JuiceCat/p/12000953.html "安装ROS时sudo rosdep init指令报错 最全解决方法")

## 5.运行环境设置
将ROS启动脚本的地址加到环境变量中，在我们每次启动终端时可以自动加载该变量

	echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
	source ~/.bashrc

如果不想加到.bashrc中可以在启动终端时加载一次

	source /opt/ros/indigo/setup.bash

如果使用的是zsh脚本加载的代码如下

	echo "source /opt/ros/indigo/setup.zsh" >> ~/.zshrc
	source ~/.zshrc

## 6.安装rosinstall
rosinstall是ROS中经常使用的命令行工具，它使您能够通过一个命令轻松下载ROS软件包的许多源。
	
	sudo apt-get install python-rosinstall