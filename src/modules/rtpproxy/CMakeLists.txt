cmake_minimum_required(VERSION 3.10)

project(rtpproxy)

file(GLOB SRC_FILES "*.c")

add_library(rtpproxy SHARED ${SRC_FILES})

target_link_libraries(rtpproxy PRIVATE kamailio)
target_link_libraries(rtpproxy PRIVATE srdb1)
