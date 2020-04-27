cmake_minimum_required(VERSION 3.11)
project (raylib-imgui
    VERSION 0.0.1
    DESCRIPTION "raylib-imgui"
    HOMEPAGE_URL "https://github.com/robloach/raylib-imgui"
    LANGUAGES C CXX)

# Options
option(BUILD_EXAMPLE "Example" ON)

# Examples
if(BUILD_EXAMPLE)
    add_subdirectory(example)
endif()
