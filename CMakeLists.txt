cmake_minimum_required (VERSION 3.0)
project (Eigen-start)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIR})
message("${CMAKE_MODULE_PATH}")
message("${EIGEN3_INCLUDE_DIR}")

add_executable (executable main.cpp)

target_link_libraries(executable 
    PUBLIC
        Eigen
)