# CMake version configuration
cmake_minimum_required(VERSION 3.5...3.19)
if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Define project
project(dxflib
    VERSION 3.26.4
    LANGUAGES CXX
)

# Use C++11
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Export library
add_library(dxflib STATIC
    # Sources
    src/dl_dxf.cpp
    src/dl_writer_ascii.cpp

    # Headers
    src/dl_attributes.h
    src/dl_codes.h
    src/dl_creationadapter.h
    src/dl_creationinterface.h
    src/dl_dxf.h
    src/dl_entities.h
    src/dl_exception.h
    src/dl_extrusion.h
    src/dl_global.h
    src/dl_writer_ascii.h
    src/dl_writer.h
)
target_include_directories(dxflib INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}/src")

# Alias to namespaced variant
add_library(Dxflib::Dxflib ALIAS dxflib)
