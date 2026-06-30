cmake_minimum_required(VERSION 3.14)

project(livox_sdk2 LANGUAGES CXX C)

set(CMAKE_POSITION_INDEPENDENT_CODE ON)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

message(STATUS "main project dir: " ${PROJECT_SOURCE_DIR})

if (CMAKE_CROSSCOMPILING)
	set(THREADS_PTHREAD_ARG
		"PLEASE_FILL_OUT-FAILED_TO_RUN"
		CACHE STRING "Result from TRY_RUN" FORCE)
endif()

find_package(Threads REQUIRED)

if (UNIX)
	add_compile_options(-pthread)
endif(UNIX)

add_subdirectory(sdk_core)
add_subdirectory(samples)