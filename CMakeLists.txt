cmake_minimum_required(VERSION 3.28)
project(dump.f2fs C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -D_FILE_OFFSET_BITS=64")

set(DEFAULT_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS_RELEASE "-O2")


set(BUILD_SHARED_LIBS OFF)
set(CMAKE_EXE_LINKER_FLAGS "-static")

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/out)

include(GNUInstallDirs)

file(GLOB SOURCES
        src/*.c
)

include_directories(
        ${CMAKE_SOURCE_DIR}/include
        ${CMAKE_SOURCE_DIR}/src
)

file(GLOB LIB_SOURCES
        lib/*.c
)

include_directories(${CMAKE_SOURCE_DIR}/lib)

add_executable(dump.f2fs ${SOURCES} ${LIB_SOURCES})
