cmake_minimum_required(VERSION 3.2)
project(divider_tests)

add_subdirectory(lib/googletest)
include_directories(lib/googletest/googletest/include)
set(SOURCE_FILES src/divider_tests.cpp)

add_executable(divider_tests ${SOURCE_FILES})
target_link_libraries(divider_tests division gtest_main)
install(TARGETS divider_tests DESTINATION ${PROJECT_INSTALL_BIN_DIR})

