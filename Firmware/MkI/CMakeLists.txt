cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(pico-dap)

pico_sdk_init()

# Collect all .c files from the different src subdirectories
# file(GLOB_RECURSE DAP_SOURCES    ./src/dap/*.c)
# file(GLOB_RECURSE SYS_SOURCES    ./src/sys/*.c)
# file(GLOB_RECURSE USB_SOURCES    ./src/usb/*.c)


add_executable(pico-dap
    ./src/main.c
#	${DAP_SOURCES}
#	${SYS_SOURCES}
#	${USB_SOURCES}
)

# Include all the needed directories
target_include_directories(pico-dap PRIVATE
	./include
#	./include/cmsis
#	./include/sys
#	./include/usb
)

target_link_libraries(pico-dap pico_stdlib)

# Make the linker more verbose
# set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -Wl,--verbose")

# Create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(pico-dap)
