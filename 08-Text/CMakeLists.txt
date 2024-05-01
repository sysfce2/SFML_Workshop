cmake_minimum_required(VERSION 3.16)

project(08-Text LANGUAGES CXX)

if(NOT TARGET sfml-graphics)
    find_package(SFML 2 COMPONENTS graphics REQUIRED)
endif()

add_executable(08-Text src/main.cpp src/Sokoban.cpp src/Map.cpp src/Box.cpp)
target_link_libraries(08-Text sfml-graphics sfml-audio)
target_compile_features(08-Text PRIVATE cxx_std_17)

if(WIN32 AND SFML_USE_STATIC_STD_LIBS)
    if(MSVC)
        set_property(TARGET 08-Text PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_link_libraries(08-Text PRIVATE "-static-libgcc" "-static-libstdc++")
    endif()
endif()
