cmake_minimum_required(VERSION 2.4.6)

project(webint_msgs)

find_package(catkin REQUIRED COMPONENTS roscpp message_generation std_msgs)

add_message_files(
  DIRECTORY msg
  FILES
    WebifTaskInfo.msg
)

generate_messages(DEPENDENCIES std_msgs)

catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs
)

