cmake_minimum_required(VERSION 3.12)
project(hello_world)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)

function(custom_executable target)
  add_executable(${target} src/${target}.cpp)
  ament_target_dependencies(${target} rclcpp)
  ament_target_dependencies(${target} std_msgs)
  install(TARGETS ${target} DESTINATION lib/${PROJECT_NAME})
endfunction()

custom_executable(talker)

custom_executable(listener)

custom_executable(talker_listener_composition)

ament_package()