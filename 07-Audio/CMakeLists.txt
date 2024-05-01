cmake_minimum_required(VERSION 3.16)

project(07-Audio LANGUAGES CXX)

if(NOT TARGET sfml-graphics)
    find_package(SFML 2 COMPONENTS graphics REQUIRED)
endif()

add_executable(07-Audio src/main.cpp src/Sokoban.cpp src/Map.cpp src/Box.cpp)
target_link_libraries(07-Audio sfml-graphics sfml-audio)
target_compile_features(07-Audio PRIVATE cxx_std_17)

if(WIN32 AND SFML_USE_STATIC_STD_LIBS)
    if(MSVC)
        set_property(TARGET 07-Audio PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_link_libraries(07-Audio PRIVATE "-static-libgcc" "-static-libstdc++")
    endif()
endif()
