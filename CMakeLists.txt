cmake_minimum_required(VERSION 3.0.2)
project(airstack_msgs)

add_compile_options(-std=c++17 -lstdc++fs) 

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
)

# Add service files
add_service_files(
  FILES
  RobotCommand.srv
  TrajectoryMode.srv
  TakeoffLandingCommand.srv
)

generate_messages(
    DEPENDENCIES
    std_msgs  # Or other packages containing msgs
    geometry_msgs
    geographic_msgs
    diagnostic_msgs
)


catkin_package(
 CATKIN_DEPENDS message_runtime 
)
