cmake_minimum_required(VERSION 3.10)

project(speeddial)

file(GLOB SRC_FILES "*.c")

add_library(speeddial SHARED ${SRC_FILES})

target_link_libraries(speeddial PRIVATE kamailio)
target_link_libraries(speeddial PRIVATE srdb1)
