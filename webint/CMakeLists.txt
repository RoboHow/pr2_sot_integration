cmake_minimum_required(VERSION 2.4.6)

project(webint)


find_package(catkin REQUIRED COMPONENTS roscpp dynamic_graph_bridge_msgs webint_msgs robohow_common_msgs)

catkin_package(
  CATKIN_DEPENDS robohow_common_msgs)


include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(task_sender test/task_sender.cpp)
target_link_libraries(task_sender ${catkin_LIBRARIES})
add_dependencies(task_sender ${catkin_EXPORTED_TARGETS})

add_executable(ErrorHolder src/ErrorHolder.cpp)
target_link_libraries(ErrorHolder ${catkin_LIBRARIES})
add_dependencies(ErrorHolder ${catkin_EXPORTED_TARGETS})

