# expanded xv6 on PiZeroW

- clean port on PiZeroW
- add tools

# xv6-armv6-rpi

The xv6-armv6-rpi is based on zhiyihuang/xv6_rpi_port (https://github.com/zhiyihuang/xv6_rpi_port). As the zhiyihuang version doesn't boot my Raspberry Pi B, as it supposed to do, I have done some changes in order to succefully boot my pi.

xv6_rpi_port is based on MIT xv6 (http://pdos.csail.mit.edu/6.828/2012/v6.html).
It is ported from x86 to armv6 in Raspberry Pi (RPI). The rpi port follows
the coding style of xv6 as much as possible to hide the architectural
differences between x86 and armv6. The port is not for multiprocessor yet
as RPI has only a single processor.

## ACKNOWLEDGEMENTS

xv6_rpi_port is inspired by MIT xv6 and Alex Chadwick's Baking Pi 
Tutorials (http://www.cl.cam.ac.uk/projects/raspberrypi/tutorials/os/).
Most architecture-independent code is directly from MIT xv6 though sometimes
minor adjustments were done to explicitly initialize data structures.
Some C code such as the GPU driver is based on the understanding of 
Alex Chadwick's assembly code. 

Some code for mmu and trap handling is based on the understanding of the
Plan 9 bcm port (http://plan9.bell-labs.com/sources/plan9/sys/src/9/bcm/),
though the assembly code was completely rewritten. 
David Welch's RPI code (https://github.com/dwelch67/raspberrypi) is also
inspiring for trap handling and uart driver.

## Building xv6-armv6-rpi

Get the source with:

git clone https://github.com/xt0fer/xv6-armv6-rpi.git

On an some rpi installed with Raspbian, type: 'make' to make 'kernel.img'.

Copy 'kernel.img' to the boot partition of your raspeberry pi  sdcard (don't forget to do a copy of the existing kernel.img with a different name).

Power the raspberry pi and get into the shell.

Type ls to see available commands.

You may clean the build with: 'make clean'

If you have troubles with the included libcsud.a, you may build an apropriate lib recompiling the csud available at https://github.com/Chadderz121/csud, and copy the new libcsud.a in the project root folder.

Changes in the initial commit (from zhiyihuang/xv6_rpi_port).

There was change in directory structure:
- The files on include directory was moved to project root (include directory deleted)
- The files on source directory was moved to project root (source directory deleted)
- The uprogs directory renamed to usr
- A new directory tools is created and mkfs.c is moved from usr directory to tools

There are some changed files:
- Makefile
- entry.s
- kernel.ld
- main.c
- mmu.c
- uart.c

There is also a new file
- wrapper.c
- tools/Makefile

If you spot errors please open an issue on github.

