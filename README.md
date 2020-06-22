# Linux Basics

## ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Overview 

* <b> What is Operating System ?</b>  
Operating system is an interface between user and the computer hardware. The hardware of the computer cannot understand the human readable language as it works on binaries i.e. 0's and 1's. Also it is very tough for humans to understand the binary language, in such case we need an interface which can translate human language to hardware and vice-versa for effective communication. 

* <b> Types of Operating System:</b>  
  * Single User - Single Tasking Operating System  
  * Single User - Multitasking Operating System  
  * Multi User - Multitasking Operating System  
 
## ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Linux File System Hierarchy  

|Path     | Description        |
|:-----: |:---      |
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

## ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Commands

- Basic Commands
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#basic-commands)
  - [pwd](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#1-pwd-)
  - [man](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#2-man-)
  - [clear](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#3-clear-)
  - [echo](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#4-echo-)
  - [whoami](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#5-whoami-)
  - [hostname](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#6-hostname-)
  - [uptime](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#7-uptime-)
  - [date](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#8-date-)
  - [cal](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#9-cal-)
  - [id](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#10-id-)
  - [last](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#11-last-)
  - [touch](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#12-touch-)
  - [cat](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#13-cat-)
  - [mkdir](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#14-mkdir-)
  - [ls](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#15-ls-)
  - [cp](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#16-cp-)
  - [mv](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#17-mv-)
  - [rmdir](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#18-rmdir-)
  - [rm](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#19-rm-)
  - [cd](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#20-cd-)
  - [history](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#21-history-)
  - [grep](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#22-grep-)
  - [find](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#23-find-)
  - [ping](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#24-ping-)
  - [df](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#25-df-)
  - [wget](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#26-wget-)
  - [ifconfig](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#27-ifconfig-)
  - [du](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#28-du-)
  - [free](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#29-free-)
  - [top](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#30-top-)
  - [kill](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#31-kill-)
  - [ps](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#32-ps-)
  - [groupadd](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#33-groupadd-)
  - [useradd](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#34-useradd-)
  - [userdel](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#35-userdel-)
  - [usermod](https://github.com/krishnaprasadkv/linux-commands/blob/master/Basic-commands.md#36-usermod-)
  

- LS Command
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/ls.md#listing-files-and-directories)
  - [Working with ls command](https://github.com/krishnaprasadkv/linux-commands/blob/master/ls.md#working-with-ls-command)
 
- Filter Commands
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#filter-commands)
  - [less](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#less-)  
  - [more](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#more-)  
  - [head](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#head-)  
  - [tail](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#tail-)  
  - [sort](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#sort-)  
  - [cut](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#cut-)  
  - [sed](https://github.com/krishnaprasadkv/linux-commands/blob/master/filtercommands.md#sed-)

  
- GREP Command
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/grep.md#grep-)
  - [Working with grep command](https://github.com/krishnaprasadkv/linux-commands/blob/master/grep.md#examples-of-grep)

- Find Command 
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/findcommand.md#find-command-)
  - [Working with find command](https://github.com/krishnaprasadkv/linux-commands/blob/master/findcommand.md#working-with-find-command)

- File Permissions
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/filepermissions.md#overview)
  - [Absolute Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/filepermissions.md#absolute-mode)
  - [Symbolic Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/filepermissions.md#symbolic-mode)

- Changing Ownership and Group
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/filepermissions.md#file-permissions-) 
  - [Change the owner of a file](https://github.com/krishnaprasadkv/linux-commands/blob/master/changing-ownership-and-group.md#change-the-owner-of-a-file)
  - [Change the owner and group of a File](https://github.com/krishnaprasadkv/linux-commands/blob/master/changing-ownership-and-group.md#change-the-owner-and-group-of-a-file)
  - [Change the group of a file](https://github.com/krishnaprasadkv/linux-commands/blob/master/changing-ownership-and-group.md#change-the-group-of-a-file)
  - [Change symbolic links ownership](https://github.com/krishnaprasadkv/linux-commands/blob/master/changing-ownership-and-group.md#change-symbolic-links-ownership)
  - [Recursively change the file ownership](https://github.com/krishnaprasadkv/linux-commands/blob/master/changing-ownership-and-group.md#recursively-change-the-file-ownership)


- VI Editor
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#overview)
  - [Insert Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#insert-mode)
  - [Command Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#command-mode)
  - [Extended Mode](https://github.com/krishnaprasadkv/linux-commands/blob/master/vi.md#extended-mode)


- Linux Links
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/links.md#overview) 
  - [Types of Links](https://github.com/krishnaprasadkv/linux-commands/blob/master/links.md#types-of-links)
  - [Difference between soft link and hard link ](https://github.com/krishnaprasadkv/linux-commands/blob/master/links.md#difference-between-soft-link-and-hard-link)
  - [Working with Links](https://github.com/krishnaprasadkv/linux-commands/blob/master/links.md#working-with-inks)

- MANAGING PROCESS 
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/managingprocess.md#overview)
  - [Types of processes](https://github.com/krishnaprasadkv/linux-commands/blob/master/managingprocess.md#types-of-processes)
  - [Working with ps command](https://github.com/krishnaprasadkv/linux-commands/blob/master/managingprocess.md#working-with-ps-command)

- Signals In Linux
  - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#overview)  
  - [Few Important Signals](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#few-important-signals-with-its-descriptions)
  - [Using most common signals](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#using-most-common-signals)
  - [Working with signals](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#working-with-signals)
  - [Setting up the priority of a process](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#setting-up-the-priority-of-a-process)
  - [Working with renice](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#working-with-renice)

  - Working Top Command 
   - [Overview](https://github.com/krishnaprasadkv/linux-commands/blob/master/topcommand.md#overview)
   - [Top Command Explanation](https://github.com/krishnaprasadkv/linux-commands/blob/master/topcommand.md#top-command-explanation)
   - [Top Command Task's Property](https://github.com/krishnaprasadkv/linux-commands/blob/master/topcommand.md#top-command-task's-property)
   - [Working With Top Command](https://github.com/krishnaprasadkv/linux-commands/blob/master/topcommand.md#working-with-top-command)