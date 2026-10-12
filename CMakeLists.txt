cmake_minimum_required(VERSION 3.28)
project(UnnamedProject LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

include(FetchContent)
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 3.1.0
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(SFML)

# If you want to add a new .cpp file to compile, write it in the parantheses after the main.cpp with a space in between.
# (But you don't need to add the .h files.)
add_executable(main src/main.cpp)
target_compile_features(main PRIVATE cxx_std_17)

# Add new modules after the Graphics one as "SFML::Audio" following a space.
target_link_libraries(main PRIVATE SFML::Graphics)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT main)
