cmake_minimum_required(VERSION 3.10)

project(ims_usrloc_pcscf)

file(GLOB SRC_FILES "*.c")

add_library(ims_usrloc_pcscf SHARED ${SRC_FILES})

target_link_libraries(ims_usrloc_pcscf PRIVATE kamailio)
target_link_libraries(ims_usrloc_pcscf PRIVATE srdb1)
