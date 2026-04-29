cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_leds C CXX)

# NOTE:
# The current source code uses Arduino APIs (setup/loop, Keypad library).
# This CMake file provides a clean project scaffold but the firmware should
# be built with the Arduino-Pico toolchain (or adapted to native Pico SDK APIs).

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

add_executable(${PROJECT_NAME}
  src/main.cpp
)

target_include_directories(${PROJECT_NAME} PRIVATE include)
