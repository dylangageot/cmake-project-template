cmake_minimum_required(VERSION 3.2)

project(cmake-project-template)

set(CMAKE_CXX_STANDARD 17)

# Code coverage flags.
option(CODE_COVERAGE "Enable code coverage" OFF)
if((${CODE_COVERAGE} STREQUAL "ON") AND (${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU"))
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -fprofile-arcs -ftest-coverage")
endif()

# Installation folders.
set(PROJECT_INSTALL_INCLUDE_DIR include)
set(PROJECT_INSTALL_BIN_DIR bin)
set(PROJECT_INSTALL_LIB_DIR lib)

# Destination directories for compiled libraries and binaries.
set(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_BINARY_DIR}/lib)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_BINARY_DIR}/bin)

# Project headers directories.
set(PROJECT_HEADERS_DIRS ${PROJECT_SOURCE_DIR}/src/division)

include_directories(${PROJECT_INSTALL_INCLUDE_DIR})
include_directories(${PROJECT_HEADERS_DIRS})

add_subdirectory(src)
add_subdirectory(test)


