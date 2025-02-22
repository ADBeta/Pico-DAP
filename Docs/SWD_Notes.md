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
0x0C    RDBUFF
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
`0x81` `0x1E000000 WRITE` NOTE: Why is this 1E when bit 28 29 set????


## Read from AP
`DP (master)` must send 


## Function Ideas
Init function sends multiple bytes of 0xFF

Struct packed with bit structure
read/write functions are calls to a generic backend function
Functions return ack bits as an enum type




## DAP HID Protocol
### Commands
```
0x00    DAP_Info                Requests ID from the DAP Device
0x01    DAP_HostStatus          Sets the host status (e.g., LED indicators)
0x02    DAP_Connect             Connects to the debug target (SWD or JTAG)
0x03    DAP_Disconnect          Disconnects from the debug target
0x04    DAP_TransferConfigure   Configures SWD/JTAG transfer settings
0x05    DAP_Transfer            Performs a single or multiple SWD/JTAG transfers
0x06    DAP_TransferBlock       Performs a block transfer over SWD/JTAG
0x07    DAP_TransferAbort       Aborts an ongoing SWD/JTAG transfer
0x08    DAP_WriteABORT          Writes to the Debug Port (DP) Abort register
0x09    DAP_Delay               Inserts a delay (in microseconds)

0x12	DAP_SWO_Transport       Selects SWO transport protocol
0x13	DAP_SWO_Mode            Configures the SWO mode
0x14	DAP_SWO_Baudrate        Sets the SWO baud rate
0x15	DAP_SWO_Control         Controls SWO trace capture
0x16	DAP_SWO_Status          Gets the status of SWO trace

0x0A    DAP_ResetTarget         Asserts a hardware reset on the target
0x0B    DAP_SWJ_Pins            Controls SWD/JTAG pins
0x0C    DAP_SWJ_Clock           Sets the SWD/JTAG clock frequency
0x0D    DAP_SWJ_Sequence        Sends a sequence of SWD/JTAG bits
0x0E    DAP_SWD_Configure       Configures the SWD interface
0x0F    DAP_JTAG_Sequence       Sends JTAG scan chain sequences
0x10    DAP_JTAG_Configure      Configures JTAG scan chain settings
0x11    DAP_JTAG_IDCODE         Reads the JTAG IDCODE

0x17    DAP_SWO_CaptureStart    Starts SWO trace capture
0x18    DAP_SWO_CaptureStop     Stops SWO trace capture
0x19    DAP_SWO_Read            Reads available SWO trace data

0xFF    DAP_Unknown             Placeholder for unknown or invalid command
```



----
ADBeta (c) 2025
