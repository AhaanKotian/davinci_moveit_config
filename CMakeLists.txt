cmake_minimum_required(VERSION 3.1.3)
project(davinci_moveit_config)



find_package(catkin REQUIRED COMPONENTS
	moveit_ros_planning_interface 
	moveit_ros_move_group
	cmake_modules
	interactive_markers
	moveit_core
	moveit_ros_perception
	moveit_ros_planning_interface
	pluginlib
	roscpp
	std_msgs
	moveit_visual_tools
)

catkin_package()

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(custom_move_group src/custom_move_group.cpp)
target_link_libraries(custom_move_group ${catkin_LIBRARIES} ${Boost_LIBRARIES})
install(TARGETS custom_move_group DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "setup_assistant.launch" EXCLUDE)
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
