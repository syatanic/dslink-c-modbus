cmake_minimum_required(VERSION 3.0.0)
project(dslink-c-modbus C)

include("${CMAKE_CURRENT_LIST_DIR}/")

include_directories("include")

set(SRC "src/main.c")

add_executable(dslink-c-modbus ${SRC})
add_dependencies(dslink-c-modbus sdk_dslink_c-static)

target_link_libraries(dslink-c-modbus sdk_dslink_c-static)
target_link_libraries()