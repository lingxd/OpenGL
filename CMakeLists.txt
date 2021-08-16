cmake_minimum_required(VERSION 3.20)
project(OpenGL)

set(CMAKE_CXX_STANDARD 14)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

find_package(OpenGL REQUIRED)

add_subdirectory(${PROJECT_SOURCE_DIR}/Dependencies/glfw)

include_directories(${PROJECT_SOURCE_DIR}/Dependencies/glfw/include)

add_executable(OpenGL src/Application.cpp)

target_link_libraries(OpenGL
        glfw
        ${OPENGL_glu_LIBRARY}
        ${GLFW_LIBRARY}
        OpenGL::GL)

