# Copyright 2019, 2021 Peter Dimov
# Distributed under the Boost Software License, Version 1.0.
# See accompanying file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt

cmake_minimum_required(VERSION 3.5...3.16)

# The default build type must be set before project()
if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR AND NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif()

project(Boost VERSION 1.77.0 LANGUAGES CXX)

set(BOOST_SUPERPROJECT_VERSION ${PROJECT_VERSION})
set(BOOST_SUPERPROJECT_SOURCE_DIR ${PROJECT_SOURCE_DIR})

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/tools/cmake/include)

option(BOOST_WITH_SHARED_LIBRARIES "Build shared version of the Boost libraries." OFF)
option(BOOST_WITHOUT_APPS "Build Boost without apps." OFF)
option(BOOST_WITHOUT_INSTALL_ALL "Build Boost without installing all artifacts." OFF)
option(BOOST_WITHOUT_INSTALL_FILES "Build Boost without installing files." OFF)
option(BOOST_WITHOUT_INSTALL_HEADERS "Build Boost without installing headers." OFF)
option(BOOST_WITHOUT_INSTALL_LIBRARIES "Build Boost without installing libraries." OFF)

if(BOOST_WITH_SHARED_LIBRARIES)
  set(BUILD_SHARED_LIBS ON)
else()
  set(BUILD_SHARED_LIBS OFF)
endif()

include(BoostRoot)
