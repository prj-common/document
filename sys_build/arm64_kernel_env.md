# arm64 kernel

## install qemu  
### For Mint
```
sudo apt-get install qemu-system-arm  
```
### install from source code
```
git clone http://git.qemu.org/git/qemu.git  
cd qemu  
./configure --help  
./configure --target-list=aarch64-softmmu  
make  
sudo make install  
```

## install toolchain  
cd ~  
mkdir bin  
cd bin  
wget http://releases.linaro.org/14.09/components/toolchain/binaries/gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux.tar.xz  
tar -Jxf gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux.tar.xz  
rm gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux.tar.xz  
cd gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux/bin/  
pwd  
edit file ~/.profile, add the following content,
```
PATH="$PATH:/home/zzy/bin/gcc-linaro-aarch64-linux-gnu-4.9-2014.09_linux/bin"
```
reboot PC
<!-- source ~/.profile !-->
<!--
## build rootfs  
$ git clone git://git.buildroot.net/buildroot buildroot.git  
  $ cd buildroot.git  
  $ make menuconfig  

  Configure it  

  * Target Options -> Target Architecture(AArch64)  
  * Toolchain -> Toolchain type (External toolchain)  
  * Toolchain -> Toolchain (Linaro AArch64 14.02)  
  * System configuration -> Run a getty (login prompt) after boot  
    (BR2_TARGET_GENERIC_GETTY)  
  * System configuration -> getty options -> TTY Port (ttyAMA0)  
    (BR2_TARGET_GENERIC_GETTY_PORT)  
  * Target Packages -> Show packages that are also provided by busybox  
    (BR2_PACKAGE_BUSYBOX_SHOW_OTHERS)  
  * Filesystem images -> cpio the root filesystem (for use as an initial RAM  
    filesystem) (BR2_TARGET_ROOTFS_CPIO)  
    $ make  
!-->

## build kernel  
make directory for work, and change to it.  
git clone https://github.com/sys-build/kern4.1_arm64_env.git  
cd kern4.1_arm64_env/linux-4.1.16/  
chage "CONFIG_INITRAMFS_SOURCE" to the right directory  
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- O=../out zzy_defconfig  
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- O=../out -j4 Image  
