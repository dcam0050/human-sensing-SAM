# add_executable(SimpleCLMYarpGaze SimpleCLMYarpGaze.cpp)
add_executable(CLMGaze CLMGaze.cpp)
find_package(ICUB)
# Local libraries
include_directories(${CLM_SOURCE_DIR}/include)

include_directories(../../lib/local/CLM/include)

include_directories(${YARP_INCLUDE_DIRS})

include_directories(${ICUB_INCLUDE_DIRS})

			
target_link_libraries(CLMGaze CLM)

target_link_libraries(CLMGaze dlib)


if(WIN32)
    target_link_libraries(CLMGaze ${OpenCVLibraries})
endif(WIN32)
if(UNIX)
    target_link_libraries(CLMGaze ${OpenCV_LIBS} ${Boost_LIBRARIES} ${TBB_LIBRARIES} ${YARP_LIBRARIES})
endif(UNIX)

install (TARGETS CLMGaze DESTINATION bin)
