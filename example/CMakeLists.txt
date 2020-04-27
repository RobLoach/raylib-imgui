# raylib
find_package(raylib 3.0.0 QUIET)
if (NOT raylib_FOUND)
    set(BUILD_EXAMPLES OFF CACHE BOOL "" FORCE) # don't build the supplied examples
    set(BUILD_GAMES    OFF CACHE BOOL "" FORCE) # or games
    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../vendor/raylib ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/raylib)
endif()

# Setup the example
add_executable(raylib-imgui-example
    raylib-imgui-example.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/imgui/imgui.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/imgui/imgui_widgets.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/imgui/imgui_draw.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/imgui/imgui_demo.cpp
    )

target_include_directories(raylib-imgui-example PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/..
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/imgui
)

# Link against the static library.
target_link_libraries(raylib-imgui-example raylib)
