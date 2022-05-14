cmake_minimum_required(VERSION 3.14)
project(ExampleProject)

set(CMAKE_CXX_STANDARD 11)

# include_directories(src)
set(INCLUDE_DIR ${CMAKE_SOURCE_DIR}/include)
include_directories(${INCLUDE_DIR})

# add_subdirectory(src)
add_subdirectory(tst)
add_subdirectory(lib/googletest)