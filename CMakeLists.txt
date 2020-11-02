cmake_minimum_required(VERSION 3.2)

project(cmake-project-template)

set(CMAKE_CXX_STANDARD 17)

# Code coverage flags.
option(CODE_COVERAGE "Enable code coverage" OFF)
if((${CODE_COVERAGE} STREQUAL "ON") AND (${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU"))
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -fprofile-arcs -ftest-coverage")
endif()

# Installation folders.
set(INSTALL_INCLUDE_DIR include)
set(INSTALL_BIN_DIR bin)
set(INSTALL_LIB_DIR lib)

# Destination directories for compiled libraries and binaries.
set(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_BINARY_DIR}/lib)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_BINARY_DIR}/bin)

add_subdirectory(src)
add_subdirectory(test)


