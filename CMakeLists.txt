cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led C CXX)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# This repository currently contains Arduino-style firmware (setup/loop + Keypad library)
# intended for simulation in Wokwi's Arduino environment.
# If you migrate to Pico SDK, keep src/main.cpp logic unchanged and adapt HAL calls.

add_custom_target(info ALL
  COMMAND ${CMAKE_COMMAND} -E echo "Use Wokwi/Arduino Pico core to build src/main.cpp"
)
