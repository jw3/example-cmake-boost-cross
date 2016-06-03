cmake_minimum_required(VERSION 3.5)
project(example)

set(CMAKE_SYSTEM_NAME Windows)
set(CMAKE_C_COMPILER i686-w64-mingw32-gcc)
set(CMAKE_CXX_COMPILER i686-w64-mingw32-g++)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --static")

add_executable(example main.cpp)
target_link_libraries(example boost_log boost_log_setup boost_thread_win32 boost_system)
set_target_properties(example PROPERTIES OUTPUT_NAME example.exe)
