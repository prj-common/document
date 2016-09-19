# embedded environment for arm32  

## install qemu  
sudo apt-get install qemu  

## install toolchain  
<!--
wget -c  http://releases.linaro.org/14.09/components/toolchain/binaries/gcc-linaro-arm-none-eabi-4.9-2014.09_linux.tar.xz  
tar -Jxf gcc-linaro-arm-none-eabi-4.9-2014.09_linux.tar.xz  
PATH="$PATH:/home/zzy/bin/gcc-linaro-arm-none-eabi-4.9-2014.09_linux/bin"  
!-->
sudo apt-get insatll gcc-arm-linux-gnueabi  
sudo apt-get install libc6-dev-armel-cross  

## get code  
git clone https://github.com/sys-build/embedded_env_arm32.git  

## build  
arm-linux-gnueabi-as -o test.o test.s  
arm-linux-gnueabi-ld -Ttext=0x0 -o test.elf test.o  
arm-linux-gnueabi-nm test.elf  
arm-linux-gnueabi-objcopy -O binary test.elf test.bin  
dd if=/dev/zero of=flash.bin bs=4096 count=4096  
dd if=test.bin of=flash.bin bs=4096 conv=notrunc   

## run in qemu  
qemu-system-arm -M connex -pflash flash.bin -nographic -serial /dev/null  

## qemu commands  
help             // help info  
info registers   // review registers  
quit             // quit  
xp /fmt address  // dump memory  
system_reset     // reset  
