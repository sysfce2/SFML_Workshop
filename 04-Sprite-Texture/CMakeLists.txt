cmake_minimum_required(VERSION 3.16)

project(04-Sprite-Texture LANGUAGES CXX)

if(NOT TARGET sfml-graphics)
    find_package(SFML 2 COMPONENTS graphics REQUIRED)
endif()

add_executable(04-Sprite-Texture src/main.cpp src/Sokoban.cpp)
target_link_libraries(04-Sprite-Texture sfml-graphics)
target_compile_features(04-Sprite-Texture PRIVATE cxx_std_17)

if(WIN32 AND SFML_USE_STATIC_STD_LIBS)
    if(MSVC)
        set_property(TARGET 04-Sprite-Texture PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_link_libraries(04-Sprite-Texture PRIVATE "-static-libgcc" "-static-libstdc++")
    endif()
endif()