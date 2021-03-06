# Copyright 2017-2018 by Martin Moene
#
# https://github.com/martinmoene/value_ptr-lite
#
# Distributed under the Boost Software License, Version 1.0.
# (See accompanying file LICENSE.txt or copy at http://www.boost.org/LICENSE_1_0.txt)

cmake_minimum_required( VERSION 3.5 )

# value_ptr-lite version, updated by script/update-version.py:

set( value_ptr_lite_version "0.1.0" )

# At default, enable building and performing of tests and building of examples:

option( VALUE_PTR_LITE_BUILD_TEST    "Build and perform value_ptr-lite tests" OFF )
option( VALUE_PTR_LITE_BUILD_EXAMPLE "Build value_ptr-lite examples" OFF )

project( value_ptr_lite LANGUAGES CXX )

include( GNUInstallDirs )

set( package_name "value_ptr-lite" )
set( include_source_dir "${PROJECT_SOURCE_DIR}/include" )

# Interface library:

add_library(
    ${package_name} INTERFACE )

target_include_directories(
    ${package_name} INTERFACE "$<BUILD_INTERFACE:${include_source_dir}>" )

# Installation:

install(
    DIRECTORY ${CMAKE_SOURCE_DIR}/include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR} )

# If requested, build and perform tests, build examples:

enable_testing()

if ( VALUE_PTR_LITE_BUILD_TEST )
    add_subdirectory( test )
endif()

if ( VALUE_PTR_LITE_BUILD_EXAMPLE )
    add_subdirectory( example )
endif()

# end of file
