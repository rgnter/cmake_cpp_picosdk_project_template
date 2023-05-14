cmake_minimum_required(VERSION 3.24)

project(cmake_cpp_picosdk_project_template
        VERSION      1.0.0
        LANGUAGES    CXX C ASM
        DESCRIPTION  "My CMake PicoSDK Project"
        HOMEPAGE_URL "https://example.com")

# Third-party targets
add_subdirectory(3rd-party)

# Project properties target
add_library(project_properties INTERFACE)
target_compile_features(project_properties
        INTERFACE)
target_compile_definitions(project_properties INTERFACE
        PICO_DEFAULT_UART_TX_PIN=16
        PICO_DEFAULT_UART_RX_PIN=17)


pico_sdk_init()

# Program target
add_executable(program
        src/pico/main.cpp)
target_link_libraries(program
        PUBLIC project_properties
        PRIVATE pico_stdlib)
