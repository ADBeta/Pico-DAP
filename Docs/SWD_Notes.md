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
- SWCLK - Max 60MHz clock signal
- SwDIO - Bidirectional data signal - SET by `DP` on Rising Edge, Read by `DP` on falling edge
```
RQST Phase:    8 bit          [Start (1)] [AP(1)/DP(0)] [R(1)/W(0)] [AP/DP ADDR][AP/DP ADDR] [Odd Parity] [Stop (0)] [Park (1)]
ACK Phase:     3 bit          [OK]  [WAIT (Retry)] [FAULT]
DATA Phase:    32 bit         LSB First
PARITY:        1 bit odd

Extra Trn clock cycle when DDR Changes
```


## Registers
```
0x00

0x04    CTRL/STAT
```


## Init Procedure
**Switching from JTAG to DAP**  
1) Send 50 CLK Cycles with SWDIO HIGH
2) Send 16-bit JTAG->SWD Sequence
3) Send 50 CLK Cycles with SWDIO HIGH
`0b0111 1001 1110 0111`

**Read Debug Identity**  
Read Register 0x00 on DP  
`0xA5` `0x00000000 READ`

**Power up Debug Domain**  
Set CDBGRSTREQ and CDBGRSTACK Bits in CTRL/STAT Address  
`0x81` `0x00000078 (MSB)`




## Function Ideas
Struct packed with bit structure
read/write functions are calls to a generic backend function
Functions return ack bits as an enum type
