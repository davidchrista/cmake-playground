cmake_minimum_required(VERSION 3.16)

include(FetchContent)

project(CMakePlayground VERSION 0.1.0 DESCRIPTION "CMake test project")

FetchContent_Declare(
  jwt-cpp
  GIT_REPOSITORY https://github.com/Thalhammer/jwt-cpp.git
  GIT_TAG v0.6.0
)
FetchContent_GetProperties(jwt-cpp)
if(NOT jwt-cpp_POPULATED)
  FetchContent_Populate(jwt-cpp)
endif()
add_subdirectory("${jwt-cpp_SOURCE_DIR}" "${jwt-cpp_BINARY_DIR}")

add_library(lib STATIC "lib/lib.cpp" "lib/lib.h")
target_link_libraries(lib STATIC jwt-cpp)

add_executable(app "src/main.cpp")
target_link_libraries(app PRIVATE lib)
target_include_directories(app PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")
