cmake_minimum_required(VERSION 3.0.2)
project(airstack_msgs)

# if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
#   add_compile_options(-Wall -Wextra -Wpedantic)
# endif()

add_compile_options(-std=c++17 -lstdc++fs) 

# find_package(ament_cmake REQUIRED)
# find_package(std_msgs REQUIRED)
# find_package(geometry_msgs REQUIRED)
find_package(diagnostic_msgs REQUIRED)
find_package(catkin REQUIRED COMPONENTS
    geographic_msgs
    geometry_msgs
    message_generation
    roscpp
    rospy
    sensor_msgs
    roslib
    std_msgs
    )
# find_package(rosidl_default_generators REQUIRED)

# rosidl_generate_interfaces(${PROJECT_NAME}
# "msg/Odometry.msg"
# "msg/FixedTrajectory.msg"
# "msg/TrajectoryXYZVYaw.msg"
# "msg/WaypointXYZVYaw.msg"
# "msg/KeepOutZone.msg"
# "msg/PlanRequest.msg"
# "msg/SearchMissionRequest.msg"
# "msg/BeliefMapData.msg"
# "msg/SearchPrior.msg"
# "msg/TaskAssignment.msg"
# "srv/RobotCommand.srv"
# "srv/TrajectoryMode.srv"
# "srv/TakeoffLandingCommand.srv"
# DEPENDENCIES std_msgs geometry_msgs diagnostic_msgs
# )

add_message_files(
  FILES
  Odometry.msg
  FixedTrajectory.msg
  TrajectoryXYZVYaw.msg
  WaypointXYZVYaw.msg
  KeepOutZone.msg
  PlanRequest.msg
  SearchMissionRequest.msg
  BeliefMapData.msg
  SearchPrior.msg
  TaskAssignment.msg
  # srv/RobotCommand.srv
  # srv/TrajectoryMode.srv
  # srv/TakeoffLandingCommand.srv
)

generate_messages(
    DEPENDENCIES
    std_msgs  # Or other packages containing msgs
    geometry_msgs
    geographic_msgs
    diagnostic_msgs
)


catkin_package(
#  INCLUDE_DIRS include
#  ${EIGEN3_INCLUDE_DIR}
#  LIBRARIES ${PROJECT_NAME}
 CATKIN_DEPENDS message_runtime 
#  DEPENDS system_lib
)

# if(BUILD_TESTING)
#   find_package(ament_lint_auto REQUIRED)
#   set(ament_cmake_copyright_FOUND TRUE)
#   set(ament_cmake_cpplint_FOUND TRUE)
#   ament_lint_auto_find_test_dependencies()
# endif()

# ament_package()
