# Pico-DAP
Pico-DAP is a CMSIS-DAP and Virtual COM Port (VCP) Device for programming
ARM based Microcontrollers, based on the `RP2040` Raspberry Pi Pico 
architecture, using the Pico-SDK toolchain.  

This reason for this project is to perfect the CMSIS-DAP device handling for
one specific device, without the worry of porting in the future.  
The project is open to the community and any ideas you have.  

## Flashing
`pico-dap.bin` and `pico-dap.uf2` files are available in the 
[Binaries](/Firmware/bins) directory.  
Use the `.uf2` if you are flashing via USB bootloader, or `.bin` if you are 
flashing via SWD.

## PCBs
### Pico-DAP-Zero
The original PCB for this project, using an aftermarket Pico Zero Development
board  
<div style="display: flex; align-items: center; gap: 10px;">
  <img src="/Images/Pico-DAP-Zero_Front.png" alt="Pico-DAP-Zero_Front" width="200">
  <img src="/Images/Pico-DAP-Zero_Back.png" alt="Pico-DAP-Zero_Back" width="200">
</div>

## TODO
* Move free-dap to a Pico-SDK Project
* Make a PCB for the regular Pico
* Make a PCB for a bare RP2040
* Change USB VID and PID

## Possible Changes
* Add CH32V SWIO Support
* Make specific JTAG USB Adatper

----
ADBeta (c) 2024
