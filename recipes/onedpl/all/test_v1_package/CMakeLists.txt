cmake_minimum_required(VERSION 3.8)
project(test_package CXX)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(ParallelSTL REQUIRED CONFIG)

message(STATUS "OneDPL test version: ${ONEDPL_VERSION_MAJOR}")
add_executable(${PROJECT_NAME} ../test_package/test_package.${ONEDPL_VERSION_MAJOR}.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE pstl::ParallelSTL)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_11)
