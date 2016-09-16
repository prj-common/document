## run the kernel with rootfs on arm64 qemu  
cd ..  
$qemu-system-aarch64 -machine virt -cpu cortex-a57 -machine type=virt -nographic -smp 1 -m 2048 -kernel out/arch/arm64/boot/Image --append "console=ttyAMA0"  

## quit  
C a c   // press Ctrl+a and then press c -> quit arm64 linux  
quit    // quit qemu  

## debug  
step debug  
start one console type following command  
// start kernel and stop the first instruction  
$ qemu-system-aarch64 -machine virt -cpu cortex-a57 -machine type=virt -nographic -smp 1 -m 2048 -kernel out/arch/arm64/boot/Image --append   "console=ttyAMA0" -s -S  

start another console type the following commands  
// start gdb and load vmlinux  
$ aarch64-linux-gnu-gdb  
(gdb) file out/vmlinux  
Reading symbols from /media/disk2/03study/kern4.1_arm64_env/out/vmlinux...done.  

(gdb) directory linux-4.1.16/  
// read source code  
Source directories searched: /media/disk2/03study/kern4.1_arm64_env/linux-4.1.16:$cdir:$cwd  

(gdb) target remote localhost:1234  
// access qemu guest  
Remote debugging using localhost:1234  
0x0000000040000000 in ?? ()  

(gdb) break start_kernel  
Breakpoint 2 at 0xffffffc0007ed5d8: file /media/disk2/03study/kern4.1_arm64_env/linux-4.1.16/init/main.c, line 493.  
(gdb) c  
Continuing.  

Breakpoint 2, start_kernel () at /media/disk2/03study/kern4.1_arm64_env/linux-4.1.16/init/main.c:493  
493	{  
(gdb) list  
488		vmalloc_init();  
489		ioremap_huge_init();  
490	}  

(gdb) s  
502		set_task_stack_end_magic(&init_task);  
(gdb) info r  
x0             0x34d5d91d	886429981  
x1             0x40b68000	1085702144  
x2             0x40	64  
x3             0x3f	63  
x4             0xffffffc000ac7000	-274866606080  
x5             0xffffffc00081f000	-274869391360  
x6             0xffffffc000aca000	-274866593792  
x7             0xffffffc000b624a8	-274865970008  
x8             0x0	0  
x9             0x1124	4388  
x10            0x34b5193519	226376627481  
x11            0x0	0  
x12            0x0	0  
x13            0x16	22  
x14            0x0	0  

dmesg log have no timestamp  
 echo Y > /sys/module/printk/parameters/time  

gdb study  
// todo

## my kernel code  
git clone https://github.com/zzyjsjcom/zzy_kernel_code.git  

<!--
git clone https://github.com/shihyu/GDB.git // GDB/data/快快樂樂學GDB_by_Jserv  
http://wiki.ubuntu.org.cn/index.php?title=%E7%94%A8GDB%E8%B0%83%E8%AF%95%E7%A8%8B%E5%BA%8F&variant=zh-hans  

todo  
//build busybox  
//make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- menuconfig  
//	1. static compile, BusyboxSettings->Build options->BuildBusybox as a static binary  
//	2. cancel, Networkingutilities->iptunel  
//	3. cancel, Networkingutilities->inetd  
//make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu-  
//make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- install  

resource  
http://stenliao.blogspot.tw/2014/10/run-aarch64-linux-on-qemu.html  
http://www.bennee.com/~alex/blog/2014/05/09/running-linux-in-qemus-aarch64-system-emulation-mode/  
http://suihkulokki.blogspot.tw/2014/08/testing-qemu-21-arm64-support.html  
http://blog.chinaunix.net/uid-25272011-id-3250053.html  
http://blog.csdn.net/jefbai/article/details/44901447  
http://www.tqcto.com/article/system/5715.html // make rootfs  
http://stenliao.blogspot.tw/2014/10/how-to-trace-aarch64-linux-kernel-with.html // step debug  
http://gogojesseco.blogspot.tw/2014_05_01_archive.html // step debug  
-->
