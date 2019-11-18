# ROS-Gazebo Turtlebot Walker
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Overview
This software consists of code to launch and run, record and play a turtlebot like a Roomba vacuum cleaning robot.

## Dependencies			
 Ubuntu 16.04 Xenial ([link](http://releases.ubuntu.com/16.04/))
 ROS kinetic ([link](http://wiki.ros.org/kinetic))
 Catkin ([link](http://wiki.ros.org/catkin))  
 Gazebo ([link](http://gazebosim.org/))

## Install the turtlebot stack
Open a terminal(1)
```
$sudo apt-get install ros-kinetic-turtlebot-gazebo 
```

## Building workspace and packages
These commands will make a workspace directory with name <workspace> in your <home> directory and make a turtle_walker in the src directory.

In terminal(1)
```
$ mkdir -p ~/<workspace>
$ cd <workspace>
$ mkdir src
$ catkin_make
$ cd src
$ git clone https://github.com/Pruthvi-Sanghavi/turtle_walker.git
$ cd ..
$ catkin_make
```

## Running the node
The following commands first opens up a gazebo simulator with the world and a spawned turtlebot.
Terminal(1)
```
$ cd
$ roslaunch turtlebot_gazebo turtle_world.launch
```

### Using rosrun
The following commands runs the walker node that makes the turtle bot to move in the world using rosrun.
Since ros master is already running no need to use roscore.
Terminal(2)
```
$ rosrun turtle_walker turtle_walker
```
To terminate use ctrl+c

### Using roslaunch
The following commands runs the walker node to move in the world using roslaunch

```
$ roslaunch turtle_walker turtle_walker.launch enableRosBag:=false 
```
To terminate use ctrl+c

### Generating and Playing Rosbag file

#### Genrating
The command shown below will launch the node and record a rosbag file for 30 seconds.
```
$ roslaunch turtle_walker turtle_walker.launch enableRosBag:=true
```
#### Playing 
The command given below will play the saved bag file.
In order to play the rosbag
Open a terminal to initiate ros master
```
$ roscore
```
Open another terminal
```
$ cd <workspace>
$ source devel/setup.bash
$ cd src/turtle_walker/results
$ rosbag play walk_record.bag
```
To terminate ctrl+c

To get the information about the bag file.
```
$ rosbag info walk_record.bag
```



