cmake_minimum_required(VERSION 3.15.0)
cmake_policy(SET CMP0091 NEW)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(VCPKG_TARGET_TRIPLET "x86-windows-static"  CACHE STRING "")

if (NOT DEFINED VCPKG_ROOT_DIR)
    message(FATAL_ERROR "please pass -DVCPKG_ROOT_DIR=... to specify vcpkg root dir")
endif()
set(CMAKE_TOOLCHAIN_FILE "${VCPKG_ROOT_DIR}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "")

project(cpprestdemo VERSION 0.1.0)


find_package(cpprestsdk CONFIG REQUIRED)

add_executable(cpprestdemo main.cpp)

set_property(TARGET cpprestdemo PROPERTY
  MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

target_link_libraries(cpprestdemo PRIVATE cpprestsdk::cpprest cpprestsdk::cpprestsdk_zlib_internal cpprestsdk::cpprestsdk_brotli_internal)

