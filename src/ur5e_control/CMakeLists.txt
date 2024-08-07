cmake_minimum_required(VERSION 3.0.2)
project(ur5e_control)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  sensor_msgs
  moveit_ros_planning_interface
  geometry_msgs
  controller_manager
  plotjuggler_msgs
)

catkin_package(
  CATKIN_DEPENDS roscpp rospy std_msgs sensor_msgs moveit_ros_planning_interface geometry_msgs controller_manager plotjuggler_msgs
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

catkin_install_python(PROGRAMS
  scripts/move_ur5e_joint.py
  scripts/force_avoidance.py
  scripts/forward_kinematics.py
  scripts/force_magnitude_publisher.py
  scripts/force_to_velocity_controller.py
  scripts/graphing_and_csv.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)


