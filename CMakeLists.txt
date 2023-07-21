cmake_minimum_required(VERSION 3.0)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_C_STANDARD 11)
project(main)

set(SRC_LIST src/app.c)
add_executable(app ${SRC_LIST})