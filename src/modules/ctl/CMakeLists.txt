cmake_minimum_required(VERSION 3.10)

project(ctl)

file(GLOB SRC_FILES "*.c")

add_library(ctl SHARED ${SRC_FILES})
# TODO: Should this be picked by user defined or hardcoded?
target_compile_definitions(ctl PRIVATE USE_FIFO CTL_SYSTEM_MALLOC)
target_link_libraries(ctl PRIVATE kamailio)

# TODO: Also install kamcmd binary
