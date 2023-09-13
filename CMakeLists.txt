# MinIO C++ Library for Amazon S3 Compatible Cloud Storage
# Copyright 2021 MinIO, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 3.10)
project(miniocpp VERSION 0.1.0 DESCRIPTION "MinIO C++ Client SDK for Amazon S3 Compatible Cloud Storage")
include(GNUInstallDirs)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

# prohibit in-source-builds
if("${CMAKE_BINARY_DIR}" STREQUAL "${CMAKE_SOURCE_DIR}")
  message(FATAL_ERROR "in-source builds are not allowed; you should create a separate directory for build files")
endif()

macro(set_globals)
  set(CMAKE_BUILD_TYPE_INIT Release)
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
  set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
  set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
  set(CMAKE_CXX_FLAGS_COVERAGE "${CMAKE_CXX_FLAGS_DEBUG} --coverage")
  set(CMAKE_EXE_LINKER_FLAGS_COVERAGE "${CMAKE_EXE_LINKER_FLAGS_DEBUG} --coverage")
  set(CMAKE_SHARED_LINKER_FLAGS_COVERAGE "${CMAKE_SHARED_LINKER_FLAGS_DEBUG} --coverage")
  set(CMAKE_MODULE_LINKER_FLAGS_COVERAGE "${CMAKE_MODULE_LINKER_FLAGS_DEBUG} --coverage")
endmacro()

set(requiredlibs)

if(CMAKE_COMPILER_IS_GNUCC)
  set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Werror")
  if(CMAKE_CXX_COMPILER_VERSION VERSION_GREATER_EQUAL 8.0 AND CMAKE_CXX_COMPILER_VERSION VERSION_LESS 9.0 AND NOT MINGW)
    list(APPEND requiredlibs stdc++fs)
  endif()
endif()

find_package(unofficial-curlpp CONFIG REQUIRED)
list(APPEND requiredlibs unofficial::curlpp::curlpp)

find_package(unofficial-inih CONFIG REQUIRED)
list(APPEND requiredlibs unofficial::inih::inireader)

find_package(nlohmann_json CONFIG REQUIRED)
list(APPEND requiredlibs nlohmann_json::nlohmann_json)

find_package(pugixml CONFIG REQUIRED)
list(APPEND requiredlibs pugixml)

find_package(OpenSSL REQUIRED)
if(OPENSSL_FOUND)
  include_directories(${OPENSSL_INCLUDE_DIR})
  list(APPEND requiredlibs OpenSSL::SSL OpenSSL::Crypto) # bugfix, because libcrypto is not found automatically
else()
  message(FATAL_ERROR "unable to find OpenSSL development and library files")
endif()

message(STATUS "Required libraries found: ${requiredlibs}")

include(CheckIncludeFiles)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_subdirectory(include)
add_subdirectory(src)

option(BUILD_EXAMPLES "Build examples" ON)
if(BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()

option(BUILD_TESTS "Build tests" ON)
if(BUILD_TESTS)
  add_subdirectory(tests)
endif()

option(BUILD_DOC "Build documentation" ON)
if(BUILD_DOC)
  # check if Doxygen is installed
  find_package(Doxygen)
  if(DOXYGEN_FOUND)
    # set input and output files
    set(DOXYGEN_IN ${CMAKE_CURRENT_SOURCE_DIR}/docs/Doxyfile.in)
    set(DOXYGEN_OUT ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile)

    # request to configure the file
    configure_file(${DOXYGEN_IN} ${DOXYGEN_OUT} @ONLY)
    message("Doxygen build started")

    # note the option ALL which allows to build the docs together with the application
    add_custom_target(doc_doxygen ALL
      COMMAND ${DOXYGEN_EXECUTABLE} ${DOXYGEN_OUT}
      WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
      COMMENT "Generating API documentation with Doxygen"
      VERBATIM)
  else(DOXYGEN_FOUND)
    message(WARNING "Doxygen not found; install it to generate documentation")
  endif(DOXYGEN_FOUND)
endif(BUILD_DOC)

configure_file(miniocpp.pc.in miniocpp.pc @ONLY)
install(FILES ${CMAKE_BINARY_DIR}/miniocpp.pc DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
