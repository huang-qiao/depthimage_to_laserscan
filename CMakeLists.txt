cmake_minimum_required(VERSION 2.8)
project(depthimage_to_laserscan)

#find_package(OpenCV REQUIRED)


target_include_directories(depthimage_to_laserscan
  include
)

add_library(DepthImageToLaserScan src/DepthImageToLaserScan.cpp)
#target_link_libraries(DepthImageToLaserScan ${catkin_LIBRARIES})

#add_library(DepthImageToLaserScanROS src/DepthImageToLaserScanROS.cpp)
#add_dependencies(DepthImageToLaserScanROS ${PROJECT_NAME}_gencfg)
#target_link_libraries(DepthImageToLaserScanROS DepthImageToLaserScan ${catkin_LIBRARIES})

#add_library(DepthImageToLaserScanNodelet src/DepthImageToLaserScanNodelet.cpp)
#target_link_libraries(DepthImageToLaserScanNodelet DepthImageToLaserScanROS ${catkin_LIBRARIES})

add_executable(depthimage_to_laserscan src/depthimage_to_laserscan.cpp)
#target_link_libraries(depthimage_to_laserscan DepthImageToLaserScanROS ${catkin_LIBRARIES})

#if(CATKIN_ENABLE_TESTING)
#  # Test the library
#  catkin_add_gtest(libtest test/DepthImageToLaserScanTest.cpp)
#  target_link_libraries(libtest DepthImageToLaserScan ${catkin_LIBRARIES})
#endif()

# add the test executable, keep it from being built by "make all"
#add_executable(test_dtl EXCLUDE_FROM_ALL test/depthimage_to_laserscan_rostest.cpp)

# Install targets
install(TARGETS DepthImageToLaserScan DepthImageToLaserScanROS DepthImageToLaserScanNodelet depthimage_to_laserscan
	RUNTIME DESTINATION ${MODULE_BIN_DESTINATION}
	LIBRARY DESTINATION ${MODULE_LIB_DESTINATION}
	ARCHIVE DESTINATION ${MODULE_LIB_DESTINATION})

install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION ${MODULE_INCLUDE_DESTINATION}
)
