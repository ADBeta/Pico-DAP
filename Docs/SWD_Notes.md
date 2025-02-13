# CMSIS-DAP / DAP / SWD notes

## Nodes
Communication is over one generic bus : DAP `Debug Access Port`  
Master device is DP `Debug Port`  
Slave Device(s) are AP `Access Ports`  
Packets are sent from the `DP` to the `AP`. The Packets contain the Address  

Comms can be done over `JTAG`, `AHB` and `APB`:
* JTAG
* AHB
* APB

## Port types
* JTAG     (Uses JTAG Protocol)
* SW-DP    (Uses SWD specifically)
* SWJ-DP   (Uses JTAG Or SWD)

Memory access and JTAG access are possible depending on need

## Hardware Protocol

