cmake_minimum_required( VERSION 2.8 )
project( showimg )

set( CMAKE_BUILD_TYPE Release )
set( CMAKE_CXX_FLAGS "-std=c++11 -O3" )

# opencv 
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

find_package( catkin REQUIRED
OpenCV
cv_bridge
roscpp
sensor_msgs
image_transport
)

include_directories ( include ${catkin_INCLUDE_DIRS} )
include_directories ( "/home/lee/catkin_ws/src/showimg/include" )

# eigen 
#include_directories( "/usr/include/eigen3/" )

# pcl 
#find_package( PCL REQUIRED COMPONENT common io )
#include_directories( ${PCL_INCLUDE_DIRS} )
#add_definitions( ${PCL_DEFINITIONS} )

set(CPP_SOURCES src/showimg.cpp)

add_executable( showimg ${CPP_SOURCES} )
target_link_libraries( showimg ${OpenCV_LIBS} ${catkin_LIBRARIES} )
