cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17 -pthread")

project(tethys_utils LANGUAGES CXX)
add_subdirectory(test)

add_executable(
        tethys_utils
        main.cpp
)

IF (NOT $ENV{TRAVIS})
    add_custom_command(
            TARGET tethys_utils
            POST_BUILD
            COMMAND clang-format -i ./src/*.hpp
    )
ENDIF ()
