cmake_minimum_required(VERSION 3.10)

project(jansson)

file(GLOB SRC_FILES "*.c")

find_package(PkgConfig REQUIRED)
pkg_check_modules(JANSSON REQUIRED IMPORTED_TARGET jansson)
add_library(jansson::jansson ALIAS PkgConfig::JANSSON)

add_library(jansson SHARED ${SRC_FILES})
target_link_libraries(jansson PRIVATE kamailio jansson::jansson)
