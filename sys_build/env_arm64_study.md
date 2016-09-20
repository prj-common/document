# arm32 study environment

## install toolchain  
sudo apt-get install g++-aarch64-linux-gnu  

## get code  
git clone https://github.com/sys-build/env_arm64_study.git  

## build & run  
aarch64-linux-gnu-gcc -o main hello.s main.c -static  
qemu-aarch64 main  
