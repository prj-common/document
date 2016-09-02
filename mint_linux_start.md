# 制作mint linux u盘启动盘
sudo dd if=virtual_platform/00environment/linuxmint-17.3-cinnamon-64bit.iso of=/dev/sdc bs=8M;sync  
注意: virtual_platform/00environment/linuxmint-17.3-cinnamon-64bit.iso 替换成iso镜象所在的全路径  
      /dev/sdc 替换成u盘对应的设备名  

# change apt source
Menu -> Preferences -> System Settings -> Software Sources
## change to ustc source
http://mirrors.ustc.edu.cn/linuxmint  
http://mirrors.ustc.edu.cn/ubuntu  
## update source
sudo apt-get update

# install pinyin input method
Menu -> Preferences -> Input method
install all Fcitx package
## mint 安装中文输入法
http://m.blog.csdn.net/article/details?id=51555466

# install more tools
sudo apt-get install vim  
sudo apt-get install ctags  
sudo apt-get install cscope  

# the more mint document
mint user guide[English version](https://www.linuxmint.com/documentation/user-guide/Cinnamon/english_18.0.pdf)  
mint user guide[Chinese verson](https://www.linuxmint.com/documentation/user-guide/Cinnamon/chinese_16.0.pdf)  
