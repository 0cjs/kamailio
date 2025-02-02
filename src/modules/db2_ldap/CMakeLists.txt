cmake_minimum_required(VERSION 3.10)

project(db2_ldap)

#  libsasl2-dev is required for LDAP support
find_package(PkgConfig REQUIRED)
pkg_check_modules(libsasl2 REQUIRED IMPORTED_TARGET libsasl2)
add_library(libsasl2::libsasl2 ALIAS PkgConfig::libsasl2)

#  libldap-2.4-2 is required for LDAP support
find_package(Ldap REQUIRED)

file(GLOB SRC_FILES "*.c")

add_library(db2_ldap SHARED ${SRC_FILES})
# LDAP_DEPRECATED is required for LDAP support else it will throw compile error
target_compile_definitions(db2_ldap PRIVATE LDAP_DEPRECATED)
target_include_directories(db2_ldap PRIVATE ${Ldap_INCLUDE_DIRS})
target_link_libraries(
  db2_ldap PRIVATE kamailio ${LDAP_LIBRARIES} libsasl2::libsasl2
)
target_link_libraries(db2_ldap PRIVATE srdb2)
