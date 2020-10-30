cmake_minimum_required(VERSION 3.2)

project(cmake-project-template)

set(CMAKE_CXX_STANDARD 17)

# Add coverage flags.
option(CODE_COVERAGE "Enable code coverage" OFF)
if((${CODE_COVERAGE} STREQUAL "ON") AND (${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU"))
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -fprofile-arcs -ftest-coverage")
endif()

if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set (CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR})
endif()

set(PROJECT_INSTALL_INCLUDE_DIR include)
set(PROJECT_INSTALL_BIN_DIR bin)
set(PROJECT_INSTALL_LIB_DIR lib)

set(PROJECT_HEADERS_DIRS ${PROJECT_SOURCE_DIR}/src/division)

include_directories(${PROJECT_INSTALL_INCLUDE_DIR})
include_directories(${PROJECT_HEADERS_DIRS})

add_subdirectory(src)
add_subdirectory(test)


