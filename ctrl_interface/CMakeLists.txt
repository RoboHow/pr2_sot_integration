cmake_minimum_required(VERSION 2.4.6)
project(ctrl_interface)

find_package(catkin REQUIRED COMPONENTS roscpp dynamic_graph_bridge_msgs urdfdom console_bridge)


catkin_package(
  CATKIN_DEPENDS dynamic_graph_bridge_msgs
  DEPENDS console_bridge urdfdom_model)
#catkin_package(DEPENDS sot-core)

# Search for dependencies.
#ADD_REQUIRED_DEPENDENCY("roscpp")
#ADD_REQUIRED_DEPENDENCY("std_msgs")
#ADD_REQUIRED_DEPENDENCY("sensor_msgs")
#add_required_dependency(sot-core)
#ADD_ROSPACK_DEPENDENCY("dynamic_graph_bridge")
# add_required_dependency(dynamic-graph)
#ADD_REQUIRED_DEPENDENCY("urdfdom")

# Handle rpath necessary to handle ROS multiplace packages
# libraries inclusion
#SET(CMAKE_SKIP_BUILD_RPATH  FALSE)
#SET(CMAKE_BUILD_WITH_INSTALL_RPATH FALSE)
#SET(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR}")
#SET(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)

set(SOURCES
   src/vel_bridge_main.cpp
   src/vel_bridge.cpp
   )

set(HEADERS
    src/vel_bridge.hpp)

include_directories(${catkin_INCLUDE_DIRS})

add_executable(vel_bridge ${SOURCES})
target_link_libraries(vel_bridge urdfdom_model ${catkin_LIBRARIES})

add_executable(fb_bridge src/fb_bridge.cpp src/fb_bridge_main.cpp)
add_executable(fake_sot_test src/fake_sot.cpp)

#ROSPACK_USE_DEPENDENCY(vel_bridge    "dynamic_graph_bridge")
#ROSPACK_USE_DEPENDENCY(fb_bridge     "dynamic_graph_bridge")
#ROSPACK_USE_DEPENDENCY(fake_sot_test "dynamic_graph_bridge")
#TODO: CORRECT THE ISSUE in the manifest.xml dg_bridge !!!!
TARGET_LINK_LIBRARIES(fb_bridge  ${catkin_LIBRARIES})
TARGET_LINK_LIBRARIES(fake_sot_test ${catkin_LIBRARIES})

