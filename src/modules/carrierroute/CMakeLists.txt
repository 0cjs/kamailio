cmake_minimum_required(VERSION 3.10)

project(carrierroute)

file(GLOB SRC_FILES "*.c")

add_library(carrierroute SHARED ${SRC_FILES})

target_link_libraries(carrierroute PRIVATE kamailio)
target_link_libraries(carrierroute PRIVATE srdb1 trie)
