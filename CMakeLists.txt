cmake_minimum_required(VERSION 3.11)
project(main LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Generate compile_commands.json
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Include external libraries
include_directories(external/raygui)

# Set build directory
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/out)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

# Dependencies
set(RAYLIB_VERSION 5.5)
include(FetchContent)
FetchContent_Declare(
    raylib
    DOWNLOAD_EXTRACT_TIMESTAMP OFF
    URL https://github.com/raysan5/raylib/archive/refs/tags/${RAYLIB_VERSION}.tar.gz
)

FetchContent_GetProperties(raylib)
if (NOT raylib_POPULATED)
    set(FETCHCONTENT_QUIET NO)
    FetchContent_MakeAvailable(raylib)
    set(BUILD_EXAMPLES OFF CACHE BOOL "" FORCE) # Don't build the supplied examples
endif()

# Ensure VS Code detects Raylib headers
include_directories(${raylib_SOURCE_DIR}/src)

# Collect all source files
file(GLOB_RECURSE SRC_FILES src/*.cpp src/*.h)

# Create the executable
add_executable(${PROJECT_NAME} ${SRC_FILES})

# Link Raylib
target_link_libraries(${PROJECT_NAME} raylib)

# Ensure the assets folder is copied into the build directory
add_custom_target(copy_assets ALL
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${CMAKE_SOURCE_DIR}/assets ${CMAKE_BINARY_DIR}/assets
)
add_dependencies(${PROJECT_NAME} copy_assets)

# MacOS specific settings
if (APPLE)
    target_link_libraries(${PROJECT_NAME} "-framework IOKit")
    target_link_libraries(${PROJECT_NAME} "-framework Cocoa")
    target_link_libraries(${PROJECT_NAME} "-framework OpenGL")
endif()
