cmake_minimum_required(VERSION 3.15)
project(test_package CXX)

find_package(libdispatch REQUIRED CONFIG)

# TEST_PACKAGE #################################################################
add_executable(${CMAKE_PROJECT_NAME} test_package.cpp)
set_property(TARGET ${CMAKE_PROJECT_NAME} PROPERTY CXX_STANDARD 14)
target_link_libraries(${CMAKE_PROJECT_NAME} libdispatch::libdispatch)
