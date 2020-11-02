cmake_minimum_required(VERSION 3.2)
project(division C CXX)

set(SOURCE_FILES
    division.h
    division.cpp
)

add_library(${PROJECT_NAME} SHARED STATIC ${SOURCE_FILES})
target_include_directories(${PROJECT_NAME} PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
        $<INSTALL_INTERFACE:${INSTALL_INCLUDE_DIR}>
        )
install(FILES division.h DESTINATION ${INSTALL_INCLUDE_DIR})
install(TARGETS ${PROJECT_NAME} EXPORT ${PROJECT_NAME}-config DESTINATION ${INSTALL_LIB_DIR})
install(EXPORT ${PROJECT_NAME}-config DESTINATION ${INSTALL_LIB_DIR}/cmake/${PROJECT_NAME})
