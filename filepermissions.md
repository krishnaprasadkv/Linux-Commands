# File Permissions:- 
## Overview

Unix-like operating systems, such as Linux, running on shared high-performance computers use settings called permissions to determine who can access and modify the files and directories stored in their file systems. Each file and directory in a file system is assigned "owner" and "group" attributes.

Most commonly, by default, the user who creates a file or directory is set as owner of that file or directory. When needed (for example, when a member of your research team leaves), the system's root administrator can change the user attribute for files and directories.

The group designation can be used to grant teammates and/or collaborators shared access to an owner's files and directories, and provides a convenient way to grant access to multiple users.

* Types of Files: 

| Symbol | Type of File | 
|:-----: |:---         |
| - | Normal file | 
|d | Directory |
|l | Link file (shortcut) |
| b | Block file (Harddisk, Floppy disk) |
| c | Character file (Keyboard, Mouse |
* Permissions are applied on three levels:- 
    * Owner or User level  
    * Group level  
    * Others level
* Access modes are of three types:- 
    * r read only 
    * w write/edit/delete/append 
    * x execute/run a command 
 
* Access modes are different on file and directory:- 

| Permissions | Files           | Directory |
|:-----: |:---         |:---   |
| r | Open the file | 'ls' the contents of dir |
| w | Write, edit, append, delete file | Add/Del/Rename contents of dir |
| x | To run a command/shell script | To enter into dir using 'cd' |
 

To list of files and directories
```
$ ls -ld samplefile
-rw-rw-rw- 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile

$ ls -ld sampledir/
drwxrwxrwx             1   krishnaprasadkv krishnaprasadkv         4096           May 27 14:45          sampledir/

Filetype+permission, links, owner,           group name of owner,  size in bytes, date of modification, file name
```

* Changing file/directory permissions with 'chmod' command

    * We can use the 'chmod' command which stands for 'change mode'. Using the command, we can set permissions (read, write, execute) on a file/directory for the owner, group and the world.   
`Syntax: chmod permissions filename`

* There are 2 ways to use the command -

    * Absolute mode
    * Symbolic mode

### Absolute mode

* In this mode, file permissions are not represented as characters but a three-digit octal number.

* The table below gives numbers for all for permissions types.

| Number |	Permission Type	| Symbol |
| :----: |  :-----|  :----:|
| 0	 |No Permission |	---  |
| 1	| Execute	| --x |
| 2	| Write	|-w- |
| 3	| Execute + Write	|-wx |
| 4	| Read	| r-- |
| 5	| Read + Execute |	r-x |
| 6	| Read +Write |	rw- | 
| 7	| Read + Write +Execute |	rwx | 

#### Lets see some examples by using absolute mode   
* Change the permissions of the file 'samplefile to '764'.  
$ `chmod 764 samplefile` 
```
$ ls -l samplefile
-rw-rw-rw- 1 krishnaprasadkv krishnaprasadkv    0 May 27 14:45 samplefile
$ chmod 764 samplefile
$ ls -l samplefile
-rwxrw-r-- 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
```
* '764' absolute code says the following:
    * Owner can read, write and execute (7 means rwx i.e. 4+2+1)
    * Usergroup can read and write (6 means rw i.e 4+2 )
    * others can only read (4 means r)

* Assigning full permission to the file i.e. rwx to all   
$ `chmod 777 samplefile`
```
$ ls -l samplefile
-rwxrw-r-- 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
$ chmod 777 samplefile
$ ls -l samplefile
-rwxrwxrwx 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
```

This is how you can change the permissions on file by assigning an absolute number.


### Symbolic Mode
* In the Absolute mode, you change permissions for all 3 owners. In the symbolic mode, you can modify permissions of a specific owner. It makes use of mathematical symbols to modify the file permissions.

| Operator	| Description |
| :---: |:--|
|+ |	Adds a permission to a file or directory|
|-	| Removes the permission|
|=	|Sets the permission and overrides the permissions set earlier.|

* The various owners are represented as -

| User | Denotations|
| :--: | :--|
|u	| user/owner|
|g	| group|
|o	| other|
|a	| all|

#### Lets see some examples of symbolic mode
 
$ `chmod u=rwx,g=rw,o=r samplefile` (user=rwx, group=rw and others=r) 
```
$ ls -l samplefile
-rw-r----x 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
$ chmod u=rwx,g+wx,o-x samplefile
$ ls -l samplefile
-rwxrwx--- 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
```

* Assigning full permission to the file i.e. rwx to all.   
$ `chmod ugo=rwx <file name>`
```
$ ls -l samplefile
-rwxrwx--- 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
$ chmod ugo=rwx samplefile
$ ls -l samplefile
-rwxrwxrwx 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
```
* Adding execute permission to user only.  
$ `chmod u+x samplefile`
* Removing write and execute permissions from group and other.  
`$ chmod go-wx samplefile` 
* Adding write and execute permissions from group and other.  
`$ chmod go+wx samplefile`   
* Giving only read permission to group and other.  
`$ chmod go=r samplefile` 
 
