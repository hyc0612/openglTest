cmake_minimum_required(VERSION 3.10)

# set the project name
project(openglTest)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(EXECUTABLE_NAME openglHelloWorld)

# add the executable
add_executable(${EXECUTABLE_NAME} openglTest.cpp)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories( ${EXECUTABLE_NAME} PUBLIC
                          "${PROJECT_BINARY_DIR}"
                          )

find_package(OpenGL REQUIRED)
target_include_directories(${EXECUTABLE_NAME} PUBLIC ${OPENGL_INCLUDE_DIR})
target_link_libraries(${EXECUTABLE_NAME} ${OPENGL_LIBRARIES})

# GLUT
find_package(GLUT REQUIRED)
target_include_directories(${EXECUTABLE_NAME} PUBLIC ${GLUT_INCLUDE_DIR})
target_link_libraries(${EXECUTABLE_NAME} ${GLUT_LIBRARIES})

# GLEW
find_package(GLEW REQUIRED)
target_include_directories(${EXECUTABLE_NAME} PUBLIC $ENV{GLEW_INCLUDE_DIRS})
# message(STATUS "ENV{GLEW_INCLUDE_DIRS}=$ENV{GLEW_INCLUDE_DIRS}")
target_link_libraries(${EXECUTABLE_NAME} "/usr/local/lib/libGLEW.2.1.0.dylib")

# GLFW
target_include_directories(${EXECUTABLE_NAME} PUBLIC "/usr/local/include/GLFW")
target_link_libraries(${EXECUTABLE_NAME} "/usr/local/lib/libglfw.3.3.dylib")

# GLTools
set(
    USR_INCLUDE_DIR
    /usr/local/include/
)
target_include_directories(${EXECUTABLE_NAME} PUBLIC ${USR_INCLUDE_DIR})
target_link_libraries(${EXECUTABLE_NAME} "/usr/local/lib/libgltools.dylib")
# message(STATUS "USR_INCLUDE_DIR=${USR_INCLUDE_DIR}")

# find_package(GLFW REQUIRED)
# if (GLFW_FOUND)
#     target_include_directories($(GLFW_INCLUDE_DIRS))
# endif()

