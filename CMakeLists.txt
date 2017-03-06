cmake_minimum_required( VERSION 3.0 )
project( MY_PROJECT )
set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra" )
set( CMAKE_BUILD_TYPE Debug )

find_package( PkgConfig REQUIRED )
pkg_check_modules( PKG REQUIRED gtkmm-2.4 cpputest )
include_directories( ${PKG_INCLUDE_DIRS} )

# EXECUTABLE DEFINIITION
add_executable( exe src/main.cpp )
target_link_libraries( exe ${PKG_LIBRARIES} )

# TEST EXECUTABLE DEFINITION
add_executable( test_exe src/main_test.cpp )
target_link_libraries( test_exe ${PKG_LIBRARIES} )
