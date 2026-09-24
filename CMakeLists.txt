cmake_minimum_required(VERSION 3.22)

project(VServer LANGUAGES CXX)

# C++20 — под последний Qt6
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

find_package(Qt6 REQUIRED COMPONENTS Core Network)

qt_standard_project_setup()

file(GLOB_RECURSE VSERVER_SOURCES CONFIGURE_DEPENDS
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h"
)

add_executable(vserver ${VSERVER_SOURCES})

target_include_directories(vserver PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/src")

target_link_libraries(vserver PRIVATE
    Qt6::Core
    Qt6::Network
)