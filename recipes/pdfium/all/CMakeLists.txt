cmake_minimum_required(VERSION 3.0)
project(cmake_wrapper)

include(conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

add_subdirectory(pdfium-cmake/cmake)
