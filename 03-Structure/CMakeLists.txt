cmake_minimum_required(VERSION 3.16)

project(03-Structure LANGUAGES CXX)

if(NOT TARGET sfml-graphics)
    find_package(SFML 2 COMPONENTS graphics REQUIRED)
endif()

add_executable(03-Structure src/main.cpp src/Sokoban.cpp)
target_link_libraries(03-Structure sfml-graphics)
target_compile_features(03-Structure PRIVATE cxx_std_17)

if(WIN32 AND SFML_USE_STATIC_STD_LIBS)
    if(MSVC)
        set_property(TARGET 03-Structure PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_link_libraries(03-Structure PRIVATE "-static-libgcc" "-static-libstdc++")
    endif()
endif()
