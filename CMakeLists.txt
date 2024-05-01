cmake_minimum_required(VERSION 3.16)

project(Workshop LANGUAGES CXX)

option(BUILD_SHARED_LIBS "Build shared libraries" OFF)

include(FetchContent)
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 2.6.x)
FetchContent_MakeAvailable(SFML)

add_subdirectory("01-Setup")
add_subdirectory("02-Movement")
add_subdirectory("03-Structure")
add_subdirectory("04-Sprite-Texture")
add_subdirectory("05-Map")
add_subdirectory("06-Entity")
add_subdirectory("07-Audio")
add_subdirectory("08-Text")