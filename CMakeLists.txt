cmake_minimum_required(VERSION 2.8.3)
project(pluginlib)

find_package(catkin REQUIRED COMPONENTS class_loader rosconsole roslib tinyxml)
find_package(Boost REQUIRED COMPONENTS filesystem system)

catkin_python_setup()

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES tinyxml
  CATKIN_DEPENDS class_loader rosconsole roslib
  DEPENDS Boost
)

include_directories(include ${catkin_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})

install(DIRECTORY include/pluginlib/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

install(FILES share/pluginlib/typed_class_loader_template.cpp
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
