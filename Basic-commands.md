# Basic Commands 

### 1. pwd:- 

* When you first open the terminal, you are in the home directory of your user. To know which directory you are in, you can use the *pwd* command. It gives us the absolute path, which means the path that starts from the root. The root is the base of the Linux file system. It is denoted by a forward slash( / ).   
Syntax: $ `pwd`  

### 2. man:-

* It shows the manual pages of the command.  
Syntax: $ `man pwd`  

### 3. clear:-

* *Clear* command clears all the clutter on the terminal and gives you a clean window to work on, just like when you launch the terminal.  
$ `clear` / ctrl+l

### 4. echo:- 

* *echo* is one of the most commonly and widely used built-in command for Linux bash and C shells, that typically used in scripting language and batch files to display a line of text/string on standard output or a file.    
$ `echo testing`    

### 5. whoami:-

* It displays the username of the current user.   
$ `whoami`   

### 6. hostname:-

* Display system information  
$ `hostname -a`  

### 7. uptime:-   

* Show how long the system has been running + load    
$ `uptime`   

### 8. date:-

* Show the current date and time  
$ `date`  

### 9. cal:-

* Show this month's calendar  
$ `cal` 

### 10. id:-

* Display the user and group ids of your current user.  
$ `id`  

### 11. last:-

* Display the last users who have logged onto the system.  
$ `last`

### 12. touch:- 
* Creating multiple files at same time   
`$ touch <filename> <filename> <filename>`  
`$ touch file1  file2  file3`  
 Note: to check the files use `ls` command.

### 13. cat:-
* cat (Concatenate) command is used to create a file and to display and modify the contents of a file.  
* create a file  
        `$ cat > filename`  
        Hello World    
        Ctrl+d (To save the file)   

* To display the content of the file   
`$ cat filename `
* To append the data in the already existing file  
`$ cat >> <filename>`  
Ctrl+d  (to save the changes) 

### 14. mkdir:-
* Creating a directory  
Syntax: `$ mkdir  <dir name>`  
`$ mkdir mydir `

* Making multiple directories inside a directory  
`$ mkdir -p Technology/{Devops/{docker,ansible,kubernetes},Cloud/{AWS,Azure,GCP}}   

* Check it by using tree command or ls –R command   
$ `tree Technology/`
```
Technology/
├── Cloud
│   ├── AWS
│   ├── Azure
│   └── GCP
└── Devops
    ├── ansible
    ├── docker
    └── kubernetes

8 directories, 0 files
```

### 15. ls:-

* Listing files and directories
$ `ls`

### 16 cp:-

* Copying files into directory   
Syntax: `cp <source filename> <destinatio directory>` \  
`cp file1 Technology `  

* Copying directories from one location to other    
Synatx: `cp –rvfp  <dir name> <destination name>`   
`$ cp –rvfp ./Technology /home/Technology`    

### 17. mv:-

* Moving files from one location to other (cut and Paste)  
Syntax: `$ mv  <filename>  <Destination directory>`  
`$mv file2 Technology `  
 
* Moving a Directory from one location to other   
Syntax: `#mv <dir name>  <destination dir name>`  
`$ mv ./Technology /home/Technology`  
 
* Renaming a File    
Syntax: `#mv <old name>  <new name>`  
`$ mv sample.txt kernelfile `  
 
* Renaming a Directory (The procedure and command for renaming the directory is exactly same as renaming a file.)  
Syntax: `$ mv old name  new name`    
`$ mv ktdir kerneldir `    

### 18. rmdir:-

* Use *rmdir* to delete a directory. But *rmdir* can only be used to delete an empty directory. To delete a directory containing files, use rm  
Syntax: $ `rmdir <dir name>`

### 19. rm:-

* Use the *rm* command to delete files and directory. To delete directory use $ `rm –rf dirname` (where r stands for recursive and f stands for forcefully 
Syntax: rm file3

### 20. cd:-

* use *cd* command to change the directory. For example, if you are in the *root directory*, and you want to change *users home directory*.  
$ `cd $HOME`  
* To know user home directory Run $ `pwd`.  

### 21. history:-

* History command shows all the commands that you have used in the past for the current terminal session. This can help you refer to the old commands you have entered and re-used them in your operations again.  
$ `history`  

### 22. grep:- 

* Search for pattern in file.   
Syntax: $ `grep pattern file`   
Ex: $ `grep hello sample`   

### 23. find:-

* Find files in `/home/krishnaprasadkv` that start with *sample*.   
Syntax: $ `find /home/krishnaprasadkv -name 'sample*'`

### 24. ping:-

* The `ping` command is usually used as a simple way to verify that a computer can communicate over the network with another computer or network device.    
$ `ping google.com`   

### 25. df:-

* *df* displays the amount of disk space available on the file system containing each file name argument.   
Syntax: `df [options]`   
Ex: $ `df -TH`  
 
### 26. wget:-

* The wget command downloads files served with HTTP, HTTPS, or FTP over a network.  
Syntax: `wget http://website.com/files/file.zip`   
Ex: `wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key`   

### 27. ifconfig:-

* The *ifconfig* command is used for displaying current network configuration information, setting up an ip address, netmask or broadcast address to an network interface, creating an alias for network interface, setting up hardware address and enable or disable network interfaces.  
$ `ifconfig`  

### 28. du:-

* The du command can be used to track the files and directories which are consuming excessive amount of space on hard disk drive.   
$ `du [options]`  
$ `du sh`  

### 29. free:-

* Display free and used memory ( -h for human readable, -m for MB, -g for GB.)  
$ `free -h`  

### 30. top:-

* Display and manage the top processes.   
$ `top`  

### 31. kill:-

* Kill process with process ID of pid   
$ `kill pid`

### 32. ps:-

* Display your currently running processes   
$ `ps`

* Display all the currently running processes on the system.  
$ `ps -ef`

* Display process information for processname   
$ `ps -ef | grep processname`

### 33. groupadd:-

* Create a group named "test".  
$ `groupadd test`  

### 34. useradd:-

* Create an account named *krishnaprasadkv*, with a comment of "Admin" and create the user's home directory.  
$ `useradd -c "Admin" -m krishnaprasadkv`  

### 35. userdel:-

* Delete the krishnaprasad account.   
$ `userdel krishnaprasadkv`    

### 36. usermod:-

* Add the john account to the sales group    
$ `usermod -aG devops krishnaprasadkv`   
