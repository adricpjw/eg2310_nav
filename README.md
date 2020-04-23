<a href="http://github.com/TetrisCat/auto_nav"><img src="http://emanual.robotis.com/assets/images/platform/turtlebot3/overview/turtlebot3_with_logo.png" title="FVCproductions" alt="FVCproductions"></a>

# 2020 EG2310 Group 7 Modified Navigation Stack

> Turtlebot3 Navigation stack but modified for our use

[![Build Status](http://img.shields.io/travis/badges/badgerbadgerbadger.svg?style=flat-square)](https://travis-ci.org/badges/badgerbadgerbadger) 

- Tested and ran on ROS1 Kinetic

**Navigation**

![Navigation Demo](http://g.recordit.co/XOr6LkQzB8.gif)

---

## Table of Contents 

- [Installation](#installation)
- [Usage](#usage)
- [Documentation](#Documentation)
---

## Installation

- Clone this repo to your local machine using `https://github.com/adricpjw/eg2310_nav`
- Make sure this is in your catkin workspace

### Setup

- Run the following from terminal line:

```shell
$ cd ~/catkin_ws && catkin_make
```

### Dependant Packages

**Follow the installation guide from :**

- http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup/

**Other Important Dependant Package:**

- http://wiki.ros.org/navigation 

---
## Usage

***Turtlebot3***

- Bring up turtlebot
```shell
pi@raspberrypi: ~ $ roslaunch turtlebot3_bringup  turtlebot3_robot.launch
```

- Launch Move_base node
```shell
pi@raspberrypi: ~ $ roslaunch eg2310 turtlebot3_nav_sim.launch
```

## Documentation 

### turtlebot3_nav_sim.launch
- main launch file
- removed amcl and map file, map source is from gmapping
- launches turtlebot3_slam gmapping launch file
- change model to appropriate type: `default = "burger"`
- launches move_base.launch

### move_base.launch
- Added [navfn](http://wiki.ros.org/navfn) as global planner
- Current local planner is [dwa local planner](http://wiki.ros.org/dwa_local_planner)

### dwa_local_planner_params_burger
- Reduced `max_trans_vel` to **0.13** and `min_trans_vel` to **0.08** for better performance

### costmap_common_params_burger
- Adjust `footprint` for varying size of turtlebot
- Can experiment with inflation radius and cost_scaling_factor for lethal cost distance from obstacles

### navfn_global_planner_params
- `default tolerance`: distance (in meters) away from obstacle that can be considered new goal

---
## Tests

- Used [Turtlebot Gazebo](http://wiki.ros.org/turtlebot_gazebo) for testing : http://wiki.ros.org/turtlebot_gazebo

<a href="http://wiki.ros.org/turtlebot_gazebo"><img src="https://emanual.robotis.com/assets/images/platform/turtlebot3/simulation/turtlebot3_world_bugger.png"> </a>



