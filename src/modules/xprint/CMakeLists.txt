cmake_minimum_required(VERSION 3.10)

project(xprint)

file(GLOB SRC_FILES "*.c")

add_library(xprint SHARED ${SRC_FILES})
target_link_libraries(xprint PRIVATE kamailio)
