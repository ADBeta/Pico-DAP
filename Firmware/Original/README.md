# Original Firmware
This firmware is based on [free-dap](https://github.com/ataradov/free-dap), 
written by [Alex Taradov](https://github.com/ataradov).  

The only modification made was to switch from using `bin2uf2` to using 
`picotool uf2 convert` to allow easier compilation in the modern RP2040/Pico
space.

## Compilation
```sh
cd ./make
make
```
`free-dap-rp2040.uf2` should be in the `/make/build/` directory - and a .bin
if needed.

## Note
I plan on porting this firmware to be fully compatable with the Pico-SDK
for easier compilation and community modification in the near future.  
This README will be updated as progress is made
