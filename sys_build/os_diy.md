# os diy  

## install tools  
sudo apt-get install qemu
sudo apt-get install nasm

## get code  
git clone https://github.com/sys-build/os_diy.git

## compiler and run  
cd os_diy/01_30days/day01/hello2  
make  
qemu-system-i386 os.img  

## clean  
Ctrl+C to exit  
make clean  
