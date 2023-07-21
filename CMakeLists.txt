cmake_minimum_required(VERSION 3.0)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_C_STANDARD 11)
project(main)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

# 搜索文件
file(GLOB MAIN_SRC ${CMAKE_CURRENT_SOURCE_DIR}/app/src/*.c)
# 加不加引号没有区别
# file(GLOB MAIN_HEAD "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/app/include)
add_executable(app ${MAIN_SRC})