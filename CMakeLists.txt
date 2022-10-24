cmake_minimum_required(VERSION 3.16)

project(CMakePlayground VERSION 0.1.0 DESCRIPTION "CMake test project")

add_library(lib STATIC "lib/lib.cpp" "lib/lib.h")

add_executable(app "src/main.cpp")
target_link_libraries(app PRIVATE lib)
target_include_directories(app PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")
