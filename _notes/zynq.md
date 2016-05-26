# XMD notes
    connect arm hw
    xreset 64
    source ps7_init.tcl
    ps7_init
    dow u-boot.elf
    con

    dow fsbl_0.elf
    xreset 64
    xreset 64 0x40
    fpga -f fpga.bit

