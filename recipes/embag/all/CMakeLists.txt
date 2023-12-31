cmake_minimum_required(VERSION 3.15)
project(embag LANGUAGES CXX)

find_package(Boost REQUIRED COMPONENTS iostreams headers)
find_package(lz4 REQUIRED CONFIG)
find_package(BZip2 REQUIRED CONFIG)

file(GLOB_RECURSE embag_SOURCES "lib/*.cc")
add_library(embag ${embag_SOURCES})
set_target_properties(embag PROPERTIES
    # embag does not export any symbols otherwise
    WINDOWS_EXPORT_ALL_SYMBOLS ON
)
target_compile_features(embag PUBLIC cxx_std_14)
target_link_libraries(embag PUBLIC
    Boost::iostreams
    Boost::headers
    lz4::lz4
    BZip2::BZip2
)

if (MSVC)
    # For a #if __cplusplus < 201402L check in lib/util.h
    target_compile_options(embag PRIVATE /Zc:__cplusplus)
endif()

install(TARGETS embag)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib/
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/embag
    FILES_MATCHING
    PATTERN "*.h"
    PATTERN "*.hpp"
)
