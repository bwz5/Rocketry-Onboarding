# Generated Cmake Pico project file
cmake_minimum_required(VERSION 3.13)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)
if (PICO_SDK_VERSION_STRING VERSION_LESS "1.4.0")
    message(FATAL_ERROR "Raspberry Pi Pico SDK version 1.4.0 (or later) required. Your version is ${PICO_SDK_VERSION_STRING}")
endif()
project(untitled C CXX ASM)


# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()
add_subdirectory(no-OS-FatFS/src build)
# Add executable. Default name is the project name, version 0.1
add_executable(untitled main.c
        hw_config.c
)
pico_set_program_name(untitled "untitled")
pico_set_program_version(untitled "0.1")
pico_enable_stdio_usb(untitled 1)
# Add the standard library to the build
target_link_libraries(untitled
        pico_stdlib
        hardware_i2c
        hardware_pwm
        FatFs_SPI)
pico_add_extra_outputs(untitled)
