# arm64 study

## compiler code  
change to directory arm64_code
make

## run
qemu-system-aarch64 -machine virt -cpu cortex-a57 -machine type=virt -nographic -smp 1 -m 2048 -kernel out/arch/arm64/boot/Image --append "console=ttyAMA0" -fsdev local,id=r,path=./arm64_code,security_model=none -device virtio-9p-device,fsdev=r,mount_tag=r  

mkdir /mnt  
mount -t 9p -o trans=virtio r /mnt  
cd /mnt  
./hello1  
./hello2  
./hello3  

## clean  
clean  
