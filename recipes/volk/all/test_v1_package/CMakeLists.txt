cmake_minimum_required(VERSION 3.1)
project(test_package LANGUAGES C)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(volk REQUIRED CONFIG)

add_executable(${PROJECT_NAME} ../test_package/test_package.c)
target_link_libraries(${PROJECT_NAME} PRIVATE volk::volk)

add_executable(${PROJECT_NAME}_nolibs ../test_package/test_package.c)
target_compile_definitions(${PROJECT_NAME}_nolibs PRIVATE VOLK_IMPLEMENTATION)
target_link_libraries(${PROJECT_NAME}_nolibs PRIVATE volk::volk_headers)
