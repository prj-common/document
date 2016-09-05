#list subdirectory total size by sort
du -sh * | sort -rh

#Hotkeys
F11: swich among full command screen and ordinary command screen  
Ctrl+u:  Erase the whole current line and move the cursor to the beginning of the current line.  

#chown/chmod
Use the chown command to change file owner and group information. Use the chmod command to change file access permissions such as read, write, and access.  
chown owner-user file  
chown owner-user:owner-group file  
chown owner-user:owner-group directory  
chown options owner-user:owner-group file  

#nautilus
nautilus .   // 文件管理窗口

#ls
$ ls -l  
total 600  
-rw-r--r--   1 test users  18693 Nov  8 00:36 COPYING  

#change mode
chown -R test:users test  
chmod -R u+rwx test  

#wc
-c  #print the byte counts  
-m  #print the character counts  
-l  #print the newline counts  
-L  #print the length of the longest line  
-w  #print the word counts  
--help #display this help and exit  

#head
// Display the first fifteen lines of myfile.txt.  
head -15 myfile.txt  

reference  
http://www.linfo.org/head.html  
http://www.cnblogs.com/peida/archive/2012/11/06/2756278.html  
http://www.computerhope.com/unix/uhead.htm  
http://my.oschina.net/lovedreamland/blog/366349  

#tail
tail -f a.log

#scp
$ scp  
usage: scp [-12346BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]  
           [-l limit] [-o ssh_option] [-P port] [-S program]  
           [[user@]host1:]file1 ... [[user@]host2:]file2  
// cp remote file to local  
scp user@ip:~/a.sh ~/share  
// cp local file to remote  
scp minicom.log user@ip:~/BuildCode/BuildCode  

#file
Identify a file’s type by examining specific fields within the file

#dd
dd if=input.bin of=output.bin ibs=1 count=281542 skip=17408  
if=file        输入文件名　标准输入确省  
of=file        输出文件名，标准输出确省  
ibs=n          输入块大小，n字节（默认512）  
count          只复制由count参数指定数量的输入块  
skip=n         拷贝之前越过n个输入块  

obs=n          输出块大小,n字节（默认512）  
bs=n           同时设置输入输出块大小  
cbs=n          转换缓冲区大小  
files=n        在中断之前拷贝和转换n个输入文件  
oseek=n        拷贝之前从输出文件开始查找n个块  
iseek          拷贝之前从输入文件开始查找n个块  
seek=n         等同于oseek  
cono=ascic     将EBCDIC码转换为ASCII  
ebcdic         ASCII->;EBCDIC  
ibm            ASCII转换为EBCDIC码时轻微不同的映象  
blolk          将新栈中断的ASCII码记录转换为固定长度  
unblock        将固定长度的ASCII码记录转换为新行中断记录  
lcase          变换字将至低等情况  
ucase          变换字将至高等情况  
swab           交换每对字节  
noerrir        出错时不停止处理  
sync           将每个块填充到ibs  

#nautilus
view the directory  
nautilus ~  

#history
list history command list

#man
Use n and Shift+n for the next and previous matches.
hit /, and type your search pattern.
Patterns can be regular expressions, for example, you could search for the word "option" by typing
/[Oo]ption
Or find all of the long arguments with
/(--)[a-Z]
To cancel the search, hit Ctrl+C.

#ls
ls -lh
-h, --human-readable  with -l, print sizes in human readable format  (e.g., 1K 234M 2G)

#md5sum
// check file md5 value
md5sum file_name
md5sum -c md5sums

#sha1sum
the same as md5sum

#rename
// 批量修改文件名
rename -v 's/\[Linux英文原版图书系列\].//' *.pdf

// 当前文件夹下所有名字为 xxx_check 的目录重命名为 xxx

#find
find . -maxdepth 1 -type d | grep "_check" | xargs rename 's/_check//'

There are four parts to this substitute command
s  Substitute command
/../../  Delimiter
one  Regular Expression Pattern Search Pattern
ONE  Replacement string

find
find . -name "init.project.rc"
find . -name "*[Ww][Aa][Tt][Cc][Hh][Dd][Oo][Gg]*" > watchdog_doc.txt
find . -type d -name "code"
find ./ -name ".git" | xargs rm -rf  // delete all .git directory
find ~ -maxdepth 1  -name ".*"    // only search user home directory

#disk tools
sudo fdisk -l
df -l
parted

#du
du -sh  // total disk usage size of current directory  
du -sh * // total disk usage size of every file and every subdirectory of current directory  
http://www.tecmint.com/check-linux-disk-usage-of-files-and-directories/  

#grep
grep ENABLE_SSDTESTD -nir .  
match [KEY]  
grep "\[KEY\]"  
-s: ignor prompt infomation  

grep mulitple words  
//In this example, search warning, error, and critical words in a text log file called /var/log/messages, enter:  
grep 'warning\|error\|critical' /var/log/messages  
//To just match words, add -w swith:  
grep -w 'warning\|error\|critical' /var/log/messages  
//egrep command can skip the above syntax and use the following syntax:  
egrep -w 'warning|error|critical' /var/log/messages  
//I recommend that you pass the -i (ignore case) and --color option as follows:  
egrep -wi --color 'warning|error|critical' /var/log/messages  
http://www.cyberciti.biz/faq/searching-multiple-words-string-using-grep/  

"\babc\b"  // 加前后边界，精确匹配 “abc”  
-i  // 不区分大小写  
-I  // 不搜索二进制文件  

// 搜索包含 arch_reset 但是不包含 charger  
grep "arch_reset" . -nr | grep -v  "charger"  

#ln
ln -s /media/disk2 /home/user_name/disk2

#kill
kill libreoffice  
ps -e | grep soffice.bin  
kill pid  
kill goagent in ubuntu  
netstat -nap | grep "py"  
kill -9 <process id>  

#hexdump
hexdump -C vmlinux_l50 | more  
     -C      Canonical hex+ASCII display.  Display the input offset in hexadecimal, followed by sixteen   space-separated, two column, hexadecimal bytes, followed by the same sixteen  
             bytes in %_p format enclosed in ``|'' characters.  

#tar
tar -cvf /tmp/etc.tar /etc                    // just tar, not compression  
tar -zcvf /tmp/etc.tar.gz /etc              // gzip compression  
tar -jcvf /tmp/etc.tar.bz2 /etc             // bzip2 compression  
tar -zxvf /tmp/etc.tar.gz                      // decompress etc.tar.gz file  
tar -zxvf /tmp/etc.tar.gz etc/passwd   // 将 /tmp/etc.tar.gz 内的 etc/passwd 解开而已,etc.tar.gz 内的根目录 / 是被拿掉了  
tar -zxvpf /tmp/etc.tar.gz /etc            // -p 保留原本文件属性  
split -d -b 100m  a.tar.gz                 // 切割压缩包  
cat x* > a.tar.gz                                //  切割后的分卷合并  

//decompress to directory  
mkdir aaa  
tar -zxf a.tar.gz -C aaa  // decompress a.tar to directory aaa  

// decompress to separate directory  
for A in ./1/1.tar.gz ./2/2.tar.gz ; do echo $(dirname $A); tar -zxf $A -C $(dirname $A); done  

#zip/unzip
install: sudo apt-get install zip  
zip a.zip 1.txt 2.txt 3.txt  
zip -r a.zip 1.txt 2.txt dir  
unzip a.zip  
zip -r zzy_config.zip .gitconfig .git-template .ssh/ .vim .vimrc   // backup my configs  

#find & rm
// 查找所有.git目录，并且删除  
find . -name .git -type d -print -exec rm -rf {} \;  

#md5sums
// create md5sums  
find . -type f -print0 | xargs -0 md5sum > md5sums  
// check md5sums  
md5sum -c checksums_backup.md5  
http://info.michael-simons.eu/2008/10/25/recursively-md5sum-all-files-in-a-directory-tree/

#reference
[1] http://www.cnblogs.com/peida/archive/2012/12/18/2822758.html  
[2] http://hi.baidu.com/microji/item/8bb148143a912326f7625c03  
[3] http://www.tecmint.com/history-command-examples/  
[5] http://linux.die.net/man/2/stat   //linux die 上查找 stat函数  
[6] http://zhangyu.blog.51cto.com/197148/137069  // dd 命令用法  
