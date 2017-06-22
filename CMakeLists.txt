cmake_minimum_required(VERSION 2.8.3)
project(test_node)


find_package(catkin REQUIRED COMPONENTS
  joy
  roscpp
  turtlesim
)


catkin_package(
  INCLUDE_DIRS 
#  LIBRARIES test_node
  CATKIN_DEPENDS joy roscpp turtlesim
  DEPENDS 
)

###########
## Build ##
###########


include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(teleop_joy src/teleop_joy.cpp)
target_link_libraries(teleop_joy ${catkin_LIBRARIES})

#############
## Install ##
#############


## Mark executables and/or libraries for installation
install(TARGETS teleop_joy
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

## Mark all other useful stuff for installation
install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
