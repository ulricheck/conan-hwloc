PROJECT(MyHello)
cmake_minimum_required(VERSION 3.0)

set(CMAKE_VERBOSE_MAKEFILE TRUE)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

find_package(Hwloc)

IF(HWLOC_FOUND)
    include_directories(${HWLOC_INCLUDE_DIRS})
    ADD_EXECUTABLE(main main.c)
    TARGET_LINK_LIBRARIES(main ${HWLOC_LIBRARIES})
ELSE()
    MESSAGE(FATAL_ERROR "HWLOC NOT FOUND!")
ENDIF()