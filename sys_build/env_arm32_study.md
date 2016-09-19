# arm32 study environment

## install qemu  
sudo apt-get install qemu  

## install toolchain  
sudo apt-get insatll gcc-arm-linux-gnueabi  
sudo apt-get install libc6-dev-armel-cross  

## compiler & run  
arm-linux-gnueabi-gcc -o hello hello.s main.c -static  
qemu-arm hello  
