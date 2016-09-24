# 制作mint linux u盘启动盘
sudo dd if=virtual_platform/00environment/linuxmint-17.3-cinnamon-64bit.iso of=/dev/sdc bs=8M;sync  
注意: virtual_platform/00environment/linuxmint-17.3-cinnamon-64bit.iso 替换成iso镜象所在的全路径  
/dev/sdc 替换成u盘对应的设备名  

## Mint 17 support  
Mint 17 LTS (Long Term Support till 2019)  

# install more tools
**simple edit:** sudo apt-get install gedit  
**vim:** sudo apt-get install vim  
**git:** sudo apt-get install git  
**ctags:** sudo apt-get install ctags  
**cscope:** sudo apt-get install cscope  
**basic development:** sudo apt-get install build-essential  
**Google chrome:** sudo apt-get install chromium-browser  
**ssh:** sudo apt-get install openssh-server openssh-client  
**Atom:** https://atom.io/  
**wiznote:**  
```
sudo add-apt-repository ppa:wiznote-team  
sudo apt-get update  
sudo apt-get install wiznote  
```

# install pinyin input method
Menu -> Preferences -> Input method  
install all Fcitx package  

Intall the optional components  
Input method -> Fcitx  

Reset PC  
Configure Current Input Method -> Addon -> Google pinyin  

Reset PC  
Input Method -> Google Pinyin  

Reset PC  

# install iptux
https://community.linuxmint.com/software/view/iptux

## mint 安装中文输入法
http://m.blog.csdn.net/article/details?id=51555466

# change apt source
Menu -> Preferences -> System Settings -> Software Sources
## change to ustc source
http://mirrors.ustc.edu.cn/linuxmint  
http://mirrors.ustc.edu.cn/ubuntu  
## update source
sudo apt-get update

# the more mint document
mint user guide: [English version](https://www.linuxmint.com/documentation/user-guide/Cinnamon/english_18.0.pdf)  
mint user guide: [Chinese verson](https://www.linuxmint.com/documentation/user-guide/Cinnamon/chinese_16.0.pdf)  
