cmake_minimum_required(VERSION 3.10)

project(nghttp2)

find_package(OpenSSL REQUIRED)
find_package(PkgConfig REQUIRED)

pkg_check_modules(nghttp2 REQUIRED IMPORTED_TARGET libnghttp2)
add_library(nghttp2::nghttp2 ALIAS PkgConfig::nghttp2)

pkg_check_modules(event REQUIRED IMPORTED_TARGET libevent libevent_openssl)
add_library(event::event ALIAS PkgConfig::event)

file(GLOB SRC_FILES "*.c")

add_library(nghttp2 SHARED ${SRC_FILES})
target_link_libraries(
  nghttp2 PRIVATE kamailio nghttp2::nghttp2 event::event OpenSSL::SSL
                  OpenSSL::Crypto
)
