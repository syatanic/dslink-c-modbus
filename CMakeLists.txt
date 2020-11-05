cmake_minimum_required(VERSION 3.0.0)
project(dslink-c-modbus C)

set(DSLINK_BUILD_BROKER OFF CACHE BOOL "Whether to build the broker" FORCE)
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/dslink")
include_directories("${CMAKE_CURRENT_BINARY_DIR}/dslink/include")
include_directories("${CMAKE_CURRENT_LIST_DIR}/dslink/sdk/include")
include_directories("${CMAKE_CURRENT_LIST_DIR}/dslink/deps/libuv/include")
include_directories("${CMAKE_CURRENT_LIST_DIR}/dslink/deps/mbedtls/include")
include_directories("${CMAKE_CURRENT_LIST_DIR}/dslink/deps/jansson/src")


include_directories("${CMAKE_CURRENT_LIST_DIR}/include")

include_directories(".")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=gnu99")

set(SRC "src/main.c")

add_executable(dslink-c-modbus ${SRC})
add_dependencies(dslink-c-modbus sdk_dslink_c-static)

target_link_libraries(dslink-c-modbus sdk_dslink_c-static)