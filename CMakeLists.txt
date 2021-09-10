cmake_minimum_required(VERSION 3.20)
project(OpenGL)

set(CMAKE_CXX_STANDARD 14)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(GLUT REQUIRED)

add_subdirectory(${PROJECT_SOURCE_DIR}/Dependencies/glfw)
add_subdirectory(${PROJECT_SOURCE_DIR}/Dependencies/glew)

include_directories(${PROJECT_SOURCE_DIR}/Dependencies/glfw/include)
include_directories(${PROJECT_SOURCE_DIR}/Dependencies/glew/include)
include_directories(${OPENGL_INCLUDE_DIRS})
include_directories(${GLUT_INCLUDE_DIRS})

add_executable(OpenGL src/Application.cpp)

target_link_libraries(OpenGL
        glfw
        libglew_static
        ${OPENGL_LIBRARY}
        ${GLFW_LIBRARY}
        ${GLEW_LIBRARY}
        ${GLUT_LIBRARY}
        OpenGL::GL)

