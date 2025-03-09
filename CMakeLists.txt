cmake_minimum_required(VERSION 3.17)

include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

project(pico_coremark C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMKAE_CXX_FLAGS "-O3 -Wall -Wextra")

pico_sdk_init()

add_executable(coremark
  coremark/core_list_join.c
  coremark/core_main.c
  coremark/core_matrix.c
  coremark/core_state.c
  coremark/core_util.c
  core_portme.c
  )

# pull in common dependencies
target_link_libraries(coremark pico_stdlib)
target_include_directories(coremark PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_SOURCE_DIR}/coremark)

# enable usb output, disable uart output
pico_enable_stdio_usb(coremark 1)
pico_enable_stdio_uart(coremark 0)

# create map/bin/hex/uf2 file etc.
pico_add_extra_outputs(coremark)
