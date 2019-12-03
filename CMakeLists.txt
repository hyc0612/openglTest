cmake_minimum_required(VERSION 3.10)

# set the project name
project(openglTest)

# add the executable
add_executable(openglTest1 openglTest.cpp)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(openglTest1 PUBLIC
                          "${PROJECT_BINARY_DIR}"
                          )

# GLEW
find_package(GLEW REQUIRED)
if (GLEW_FOUND)
    include_directories($ENV{GLEW_INCLUDE_DIRS})
    message(STATUS "ENV{GLEW_INCLUDE_DIRS}=$ENV{GLEW_INCLUDE_DIRS}")
endif()

link_directories("/usr/local/lib/")

LINK_LIBRARIES(libgltools.dylib)

set(
    USR_INCLUDE_DIR
    /usr/local/include/
)
include_directories(${USR_INCLUDE_DIR})
message(STATUS "USR_INCLUDE_DIR=${USR_INCLUDE_DIR}")

# find_package(GLFW REQUIRED)
# if (GLFW_FOUND)
#     include_directories($(GLFW_INCLUDE_DIRS))
# endif()