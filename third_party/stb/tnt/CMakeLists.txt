cmake_minimum_required(VERSION 3.10)
project(stb)

set(TARGET stb)

set(OUR_DIR ${CMAKE_CURRENT_SOURCE_DIR}/..)

set(PUBLIC_HDR_DIR ${OUR_DIR})

file(GLOB_RECURSE PUBLIC_HDRS ${PUBLIC_HDR_DIR}/*.h)
include_directories(${PUBLIC_HDR_DIR})

# DAZ Change, make this static lib to avoid debug build issues
add_library(${TARGET} STATIC ${OUR_DIR}/stb.c)

# The stb.c file is made a public source, so static libraries that link against stb will contain it
# within their archive. This is helpful for libraries like gltfio that are used externally.
target_sources(${TARGET} PUBLIC ${PUBLIC_HDRS} )

target_include_directories(${TARGET} PUBLIC ${PUBLIC_HDR_DIR})

# DAZ Change, because we make static lib, coopy to install dir
install(TARGETS ${TARGET} ARCHIVE DESTINATION lib/${DIST_DIR})
