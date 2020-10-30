cmake_minimum_required(VERSION 3.2)
project(division C CXX)

set(SOURCE_FILES
    division.h
    division.cpp
)

add_library(${PROJECT_NAME} SHARED STATIC ${SOURCE_FILES})
install(TARGETS ${PROJECT_NAME} DESTINATION ${PROJECT_INSTALL_LIB_DIR})
install(FILES division.h DESTINATION ${PROJECT_INSTALL_INCLUDE_DIR})
