# Linux Basics

* <b> What is Operating System ?</b>  
Operating system is an interface between user and the computer hardware. The hardware of the computer cannot understand the human readable language as it works on binaries i.e. 0's and 1's. Also it is very tough for humans to understand the binary language, in such case we need an interface which can translate human language to hardware and vice-versa for effective communication. 

* <b> Types of Operating System:</b>   
  * Single User - Single Tasking Operating System   
  * Single User - Multitasking Operating System   
  * Multi User - Multitasking Operating System   
 
 ###  Linux File System Hierarchy  

|Path       | Description           |
|:-----: |:---         |
| / |It is parent directory for all other directories.(root directory)|
| /root | It is home directory for root user and it provides working environment for root user|
| /home | It is home directory for other users and it provide working environment for other users|
| /boot |It contains bootable files for Linux. Like `GRUB (GRand Unified Boot loader)  boot.ini, ntldr` |
| /etc | It contains all configuration files. Like `User info /etc/passwd` |
| /usr | By default softwares are installed in /usr directory|
| /opt | It is optional directory for /usr and it contains third party softwares. |
| /bin | It contains commands used by all users(Binary files)|    
| /sbin | It contains commands used by only Super User (root) |
| /dev | It contains device file like `hard disk /dev/hda` |
| /proc |  It contain process files and data are not permanent, they keep changing like `information of CPU /proc/cpuinfo` |
| /var |It is containing variable data like `mails, log files` |    
| /mnt |It is default mount point for any partition. It is empty by default |
| /media |It contains all of removable media like `CD-ROM, pen drive` |
| /lib | It contains library files which are used by OS. Library files in Linux are shared object files|

### Commands

* [Basic commands](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md)
  * [Creating a files and directory](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#creating-a-files-and-directory)
  * [Copying files](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#copying-files)
  * [Renaming a File and Directory](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#renaming-a-file-and-directory)   

* [vi](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md)  
  * [Insert Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#insert-mode)
  * [Command Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#command-mode)
  * [Extended Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#extended-mode)

* [filter commands](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md)
  * [less](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#less-)  
  * [more](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#more-)  
  * [head](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#head-)  
  * [tail](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#tail-)  
  * [sort](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#sort-)  
  * [cut](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#cut-)  
  * [sed](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#sed-)
