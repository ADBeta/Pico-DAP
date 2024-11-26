# Pico-DAP Firmware
This firmware is based on [free-dap](https://github.com/ataradov/free-dap), 
written by [Alex Taradov](https://github.com/ataradov).  
Converted into a Pico-SDK Project, with changes and improvements.

## Binary files
`pico-dap.bin` and `pico-dap.uf2` are available in the [Binary](/Firmware/bins) 
directory for easy installation.

## Compilation
You will need to install [Pico-SDK](https://www.raspberrypi.com/documentation/microcontrollers/c_sdk.html)
and Optionally [picotool](https://github.com/raspberrypi/picotool) in order to compile this firmware.  
```sh
mkdir ./build
cd ./build
cmake ..
make
```
`pico-dap.bin` and `pico-dap.uf2` files should now be in the `build` directroy

## Changelog
* Changed USB Device Descriptors
* Changed VID PID for USB
* Changed VCP and DAP Status LEDs

## TODO
### HIGH PRIORITY
* Convert all IO Calls to remove hal files
* Convert all uart calls to remove uart.c/.h
* Convert fully from rp2040.h to pico-stdlib

### MEDIUM PRIORITY
* make tasks.c/.h to tidy up main task handing

### LOW PRIORITY

----
ADBeta (c) 2024
