cmake_minimum_required(VERSION 3.8)

# set the project name and version
project(stb VERSION 0.1)

set(CMAKE_CXX_STANDARD 20 FORCE)
set(CMAKE_EXPORT_COMPILE_COMMANDS 1)


file(GLOB_RECURSE stb_src_files CONFIGURE_DEPENDS "stb_image.h" "stb_src.cpp")

add_library(stb SHARED)

target_sources(stb PRIVATE ${stb_src_files})
target_include_directories(stb PUBLIC ".")
#definition for dll for exports
set_target_properties(stb PROPERTIES COMPILE_DEFINITIONS "STB_IMAGE_IMPLEMENTATION")

install(TARGETS stb
        CONFIGURATIONS Debug
        RUNTIME DESTINATION Debug/bin)