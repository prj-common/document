# arm32 study environment

## install qemu  
sudo apt-get install qemu  

## install toolchain  
sudo apt-get install g++-arm-linux-gnueabi  
<!--
sudo apt-get install libc6-dev-armel-cross  
!-->

## get code  
git clone https://github.com/sys-build/embedded_env_arm32.git  

## compiler & run
arm-linux-gnueabi-gcc -o hello hello.s main.c -static  
qemu-arm hello  

## debug  
qemu-arm -g 1234 hello  
$ arm-none-eabi-gdb  
(gdb) target remote :1234  
Remote debugging using :1234  
warning: A handler for the OS ABI "GNU/Linux" is not built into this configuration  
of GDB.  Attempting to continue with the default armv5t settings.  

0x0001044c in _start ()  
(gdb) file ./hello  
A program is being debugged already.  
Are you sure you want to change the file? (y or n) y  
Reading symbols from /home/zzy/sda7/virtual_platform/02codebase/02sys_build/embedded_env_arm32/hello...(no debugging symbols found)...done.  
(gdb) b add  
Breakpoint 1 at 0x105b4  
(gdb) c  
Continuing.  

Breakpoint 1, 0x000105b4 in add ()  
(gdb) info r  
r0             0x3	3  
r1             0xf6fff064	-150998940  
r2             0xf6fff06c	-150998932  
r3             0x105c4	67012  
r4             0xf6ffef28	-150999256  
r5             0x10d48	68936  
r6             0x0	0  
r7             0x0	0  
r8             0x0	0  
r9             0x0	0  
r10            0x96f6c	618348  
r11            0xf6ffef14	-150999276  
r12            0x0	0  
sp             0xf6ffef10	0xf6ffef10  
lr             0x105d4	67028  
pc             0x105b4	0x105b4 <add>  
cpsr           0x60000010	1610612752  
(gdb) s  
Single stepping until exit from function add,  
which has no line number information.  
0x000105d4 in main ()  
(gdb) info r  
r0             0x3	3  
r1             0x1	1  
r2             0x2	2  
r3             0x105c4	67012  
r4             0xf6ffef28	-150999256  
r5             0x10d48	68936  
r6             0x0	0  
r7             0x0	0  
r8             0x0	0  
r9             0x0	0  
r10            0x96f6c	618348  
r11            0xf6ffef14	-150999276  
r12            0x0	0  
sp             0xf6ffef10	0xf6ffef10  
lr             0x105d4	67028  
pc             0x105d4	0x105d4 <main+16>  
cpsr           0x60000010	1610612752  
(gdb)  
