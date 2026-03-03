cmake_minimum_required(VERSION 3.8)
project(people_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

# List out the message files
set(msg_files
  "msg/People.msg"
  "msg/Person.msg"
  "msg/PersonStamped.msg"
  "msg/PositionMeasurement.msg"
  "msg/PositionMeasurementArray.msg"
)

# Generate the ROS 2 interfaces
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES std_msgs geometry_msgs
)

# Export runtime dependencies
ament_export_dependencies(rosidl_default_runtime)

ament_package()