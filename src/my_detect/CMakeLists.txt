cmake_minimum_required(VERSION 3.10)
project(my_detect)

set(cv_bridge_DIR /usr/local/cv_bridge455/share/cv_bridge/cmake)
set(OpenCV_DIR "/usr/local/share/opencv4")

find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  roscpp
  rospy
  sensor_msgs
  std_msgs
)
find_package(OpenCV 4.5.5 REQUIRED)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES my_image_transport
#  CATKIN_DEPENDS cv_bridge image_transport
#  DEPENDS system_lib
)

INCLUDE_DIRECTORIES(
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_executable(my_publisher src/my_publisher.cpp)
add_executable(my_subscriber src/my_subscriber.cpp)

target_link_libraries(my_publisher ${OpenCV_LIBS})
target_link_libraries(my_publisher ${catkin_LIBRARIES})

target_link_libraries(my_subscriber ${OpenCV_LIBS})
target_link_libraries(my_subscriber ${catkin_LIBRARIES})




