cmake_minimum_required(VERSION 3.2)
project(divider)

add_subdirectory(division)
set(SOURCE_FILES main.cpp)

add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} division)
install(TARGETS ${PROJECT_NAME} DESTINATION ${PROJECT_INSTALL_BIN_DIR})
