cmake_minimum_required(VERSION 3.10)

project(gcrypt)

find_package(PkgConfig REQUIRED)
pkg_check_modules(gcrypt REQUIRED IMPORTED_TARGET libgcrypt)
add_library(gcrypt::gcrypt ALIAS PkgConfig::gcrypt)

file(GLOB SRC_FILES "*.c")

add_library(gcrypt SHARED ${SRC_FILES})
target_link_libraries(gcrypt PRIVATE kamailio gcrypt::gcrypt)
