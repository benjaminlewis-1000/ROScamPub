cmake_minimum_required(VERSION 2.8.3)
project(webcam_pub)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  cv_bridge
  image_transport
  sensor_msgs
  message_generation
)

generate_messages(
   DEPENDENCIES
   std_msgs
   sensor_msgs
)

find_package(OpenCV)

catkin_package()

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_executable(webcam src/webcam.cpp)
target_link_libraries(webcam ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})

add_executable(video src/videoStream.cpp)
target_link_libraries(video ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})

add_executable(viewer src/viewer.cpp)
target_link_libraries(viewer ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})
