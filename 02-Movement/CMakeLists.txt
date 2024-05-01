cmake_minimum_required(VERSION 3.16)

project(02-Movement LANGUAGES CXX)

if(NOT TARGET sfml-graphics)
    find_package(SFML 2 COMPONENTS graphics REQUIRED)
endif()

add_executable(02-Movement src/main.cpp)
target_link_libraries(02-Movement sfml-graphics)
target_compile_features(02-Movement PRIVATE cxx_std_17)

if(WIN32 AND SFML_USE_STATIC_STD_LIBS)
    if(MSVC)
        set_property(TARGET 02-Movement PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_link_libraries(02-Movement PRIVATE "-static-libgcc" "-static-libstdc++")
    endif()
endif()
