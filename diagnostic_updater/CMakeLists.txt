cmake_minimum_required(VERSION 2.8.3)
project(diagnostic_updater)

# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED diagnostic_msgs roscpp rostest std_msgs)

catkin_package(DEPENDS diagnostic_msgs roscpp std_msgs
               INCLUDE_DIRS include
)

include_directories(include ${catkin_INCLUDE_DIRS})
add_executable(example src/example.cpp)
target_link_libraries(example ${catkin_LIBRARIES})

catkin_add_gtest(diagnostic_updater_test test/diagnostic_updater_test.cpp)
add_rostest(test/diagnostic_updater_test.xml)

install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)
