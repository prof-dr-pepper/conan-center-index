cmake_minimum_required(VERSION 3.15)

project(test_package CXX) # if the project uses c++
find_package(stlab REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.cpp)
target_compile_definitions( ${PROJECT_NAME} INTERFACE $<$<CXX_COMPILER_ID:MSVC>:NOMINMAX> )
target_link_libraries(${PROJECT_NAME} PRIVATE stlab::stlab)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)

