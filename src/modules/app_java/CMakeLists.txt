cmake_minimum_required(VERSION 3.10)

project(app_java)

file(GLOB SRC_FILES "*.c")

# TODO: GCJ is a discontiuned project from 2018
# sudo apt install openjdk-13-jdk compiles with warnings
find_package(JNI REQUIRED)

add_library(app_java SHARED ${SRC_FILES})
target_compile_options(app_java PRIVATE -O0 -g)
target_include_directories(app_java PRIVATE JNI_INCLUDE_DIRS)
target_link_libraries(app_java PRIVATE kamailio JNI::JNI)
