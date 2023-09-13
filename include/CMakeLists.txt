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

include(CheckIncludeFiles)
include(CheckFunctionExists)

check_include_files(inttypes.h    HAVE_INTTYPES_H)
check_include_files(stdint.h      HAVE_STDINT_H)
check_include_files(stdlib.h      HAVE_STDLIB_H)
check_include_files(limits.h      HAVE_LIMITS_H)
check_include_files(sys/types.h   HAVE_SYS_TYPES_H)

check_function_exists(strtoimax   HAVE_STRTOIMAX_F)
check_function_exists(strptime    HAVE_STRPTIME_F)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/config.h.in ${CMAKE_CURRENT_SOURCE_DIR}/config.h @ONLY)

file(GLOB files "${CMAKE_CURRENT_SOURCE_DIR}/*.h")
install(FILES ${files} DESTINATION include/miniocpp)
install(FILES DESTINATION include)
