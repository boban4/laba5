cmake_minimum_required(VERSION 3.10)

project(laba5)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_TESTS "Build tests" OFF)

add_subdirectory(banking)

if(BUILD_TESTS)
  enable_testing()

  add_subdirectory(googletest/gtest)

  file(GLOB LABA5_TEST_SOURCES tests/*.cpp)

  add_executable(check ${LABA5_TEST_SOURCES})
  target_link_libraries(check banking gmock_main)

  add_test(NAME check COMMAND check)
endif()
