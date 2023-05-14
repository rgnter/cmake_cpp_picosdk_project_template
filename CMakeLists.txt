cmake_minimum_required(VERSION 3.24)

project(cmake_cpp_picosdk_project_template
        VERSION      1.0.0
        LANGUAGES    CXX C ASM
        DESCRIPTION  "My CMake PicoSDK Project"
        HOMEPAGE_URL "https://example.com")

add_subdirectory(3rd-party)

add_library(project_properties INTERFACE)
target_compile_features(project_properties
        INTERFACE)
target_compile_definitions(project_properties
        INTERFACE)


pico_sdk_init()

# Program
add_executable(program
        src/pico/main.cpp)
target_link_libraries(program
        PUBLIC project_properties
        PRIVATE pico_stdlib)
