cmake_minimum_required(VERSION 2.8.3)
project(robot_gazebo_plugin)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
  gazebo_plugins
  nav_msgs
  tf
  roscpp
)
# Depend on system install of Gazebo
find_package(gazebo REQUIRED)

catkin_package()

link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS})

add_library(diff_drive_gazebo_plugin src/diff_drive_gazebo_plugin.cpp)
target_link_libraries(diff_drive_gazebo_plugin ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})

