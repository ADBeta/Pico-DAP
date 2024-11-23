# Original Firmware
This firmware is based on [free-dap](https://github.com/ataradov/free-dap), 
written by [Alex Taradov](https://github.com/ataradov).  

The only modifications made are:  
* Switch from using `bin2uf2` to using `picotool uf2 convert`
* Change VCP and DAP Status LED Pins
* Change USB Descriptor strings
* Changed Makefile to produce `pico-dap` files instead of `free-dap`

## Compilation
```sh
cd ./make
make
```
`pico-dap.uf2`and `pico-dap.bin` should be in the `/make/build/` directory

## Note
I plan on porting this firmware to be fully compatable with the Pico-SDK
for easier compilation and community modification in the near future.  
This README will be updated as progress is made
