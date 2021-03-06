#mkfs  
mkfs -t ext4 /dev/sdb  
http://www.linfo.org/mkfs.html  
http://blog.csdn.net/asx20042005/article/details/7264867  

#fstab  
A simple /etc/fstab, using kernel name descriptors:  
/etc/fstab  
\# &lt;file system> &lt;dir>  &lt;type>    &lt;options> &lt;dump> <pass>  
/dev/sda1              /             ext4      defaults,noatime      0      1  
/dev/sda2              none          swap      defaults              0      0  
/dev/sdb              /home         ext4      defaults,noatime      0      2  

##Field definitions  
Each line in the /etc/fstab file contains the following fields separated by spaces or tabs:  
file_system    dir    type    options    dump    pass

##file system
The partition or storage device to be mounted.
dir
The mountpoint where <file system> is mounted to.
##type
The file system type of the partition or storage device to be mounted. Many different file systems are supported: ext2, ext3, ext4, btrfs, reiserfs, xfs, jfs, smbfs, iso9660, vfat, ntfs, swap and auto. The auto type lets the mount command guess what type of file system is used. This is useful for optical media (CD/DVD).
##options
Mount options of the filesystem to be used. See the mount man page. Please note that some options are specific to filesystems; to discover them see below in the aforementioned mount man page.
##dump
Used by the dump utility to decide when to make a backup. Dump checks the entry and uses the number to decide if a file system should be backed up. Possible entries are 0 and 1. If 0, dump will ignore the file system; if 1, dump will make a backup. Most users will not have dump installed, so they should put 0 for the dump entry.
##pass
Used by fsck to decide which order filesystems are to be checked. Possible entries are 0, 1 and 2. The root file system should have the highest priority 1 (unless its type is btrfs, in which case this field should be 0) - all other file systems you want to have checked should have a 2. File systems with a value 0 will not be checked by the fsck utility.

##reference
https://wiki.archlinux.org/index.php/Fstab  
https://en.wikipedia.org/wiki/Fstab  
