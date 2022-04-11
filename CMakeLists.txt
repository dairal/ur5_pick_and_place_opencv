cmake_minimum_required(VERSION 3.0.2)
project(ur5_pick_and_place_opencv)

find_package(catkin REQUIRED
  COMPONENTS
    opencv_services
    interactive_markers
    moveit_core
    moveit_ros_planning
    moveit_ros_planning_interface
    moveit_ros_perception
    rviz_visual_tools
    moveit_visual_tools
    pluginlib
    geometric_shapes
    pcl_ros
    pcl_conversions
    rosbag
    tf2_ros
    tf2_eigen
    tf2_geometry_msgs
    actionlib_msgs
    control_msgs
)

generate_messages(
  DEPENDENCIES actionlib_msgs std_msgs trajectory_msgs control_msgs  # Or other packages containing msgs
)

catkin_package(
  LIBRARIES
  INCLUDE_DIRS
  CATKIN_DEPENDS
    moveit_core
    moveit_visual_tools
    moveit_ros_planning_interface
    interactive_markers
    tf2_geometry_msgs
    actionlib_msgs
    control_msgs
    opencv_services
)

include_directories(SYSTEM ${catkin_INCLUDE_DIRS} ${Boost_INCLUDE_DIR} ${EIGEN3_INCLUDE_DIRS})

add_executable(pick_and_place_opencv src/pick_and_place_opencv.cpp)
target_link_libraries(pick_and_place_opencv ${catkin_LIBRARIES} ${Boost_LIBRARIES})

#install(TARGETS pick_and_place_opencv DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

#install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
