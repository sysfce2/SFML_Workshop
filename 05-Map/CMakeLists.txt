cmake_minimum_required(VERSION 3.16)

project(05-Map LANGUAGES CXX)

if(NOT TARGET sfml-graphics)
    find_package(SFML 2 COMPONENTS graphics REQUIRED)
endif()

add_executable(05-Map src/main.cpp src/Sokoban.cpp src/Map.cpp)
target_link_libraries(05-Map sfml-graphics)
target_compile_features(05-Map PRIVATE cxx_std_17)

if(WIN32 AND SFML_USE_STATIC_STD_LIBS)
    if(MSVC)
        set_property(TARGET 05-Map PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_link_libraries(05-Map PRIVATE "-static-libgcc" "-static-libstdc++")
    endif()
endif()
