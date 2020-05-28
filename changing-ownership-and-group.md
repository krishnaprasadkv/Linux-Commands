# Changing Ownership and Group

The chown command allows you to change the user and/or group ownership of a given file, directory, or symbolic link.
In Linux, all files are associated with an owner and a group and assigned with permission access rights for the file owner, the group members, and others.
* ### Use chown
    * Before going into ### use the chown command, let’s start by reviewing the basic syntax.
    * The chown command expressions takes the following form:
`chown [OPTIONS] USER[:GROUP] FILE(s)`

* USER is the user name or the user ID (UID) of the new owner. GROUP is the name of the new group or the group ID (GID). FILE(s) is the name of one or more files, directories or links. Numeric IDs should be prefixed with the + symbol.

    * USER - If only the user is specified, the specified user will become the owner of the given files, the group ownership is not changed.
    * USER: - When the username is followed by a colon :, and the group name is not given, the user will become the owner of the files, and the files group ownership is changed to user’s login group.
    * USER:GROUP - If both the user and the group are specified (with no space betwen them), the user ownership of the files is changed to the given user and the group ownership is changed to the given group.
    * :GROUP - If the User is omitted and the group is prefixed with a colon :, only the group ownership of the files is changed to the given group.
    * : If only a colon : is given, without specifying the user and the group, no change is made.
By default, on success, chown doesn’t produce any output and returns zero.


* Use the ls -l command to find out who owns a file or what group the file belongs to:
```
ls -l filename.txt  
-rw-r--r-- 12 root users 12.0K Apr  8 20:51 filename.txt   
|[-][-][-]-   [------] [---]
                |       |
                |       +-----------> Group
                +-------------------> Owner
``` 
Normal users can change the group of the file only if they own the file and only to a group of which they are a member. Administrative users can change the group ownership of all files.

### Change the Owner of a File 

* For changing the ownership of a file/directory, you can use the following command:
`chown user filename` 

* The following command will change the ownership of a file named *samplefile* to a owner named root and group *krishnaprasadkv*:

```
ls -l samplefile
-rw-r----x 1 krishnaprasadkv krishnaprasadkv 0 May 27 14:45 samplefile
$ sudo chown root samplefile
[sudo] password for krishnaprasadkv:
$ ls -l samplefile
-rwxrwxrwx 1 root krishnaprasadkv 0 May 27 14:45 samplefile
```

* To change the ownership of multiple files or directories, specify them as a space-separated list. The command below changes the ownership of a file named samplefile and directory dir1 to a new owner named root:

`chown root samplefile dir1`

* The numeric user ID (UID) can be used instead of the username. The following example will change the ownership of a file named file2 to a new owner with UID of 1000:

`chown 1000 file2`

* If a numeric owner exists as a user name, then the ownership will be transferred to the user name. To avoid this prefix the ID with +:

`chown 1000 file2`

### Change the Owner and Group of a File

* To change both the owner and the group of a file use the chown command followed by the new owner and group separated by a colon (:) with no intervening spaces and the target file.

`chown USER:GROUP FILE`

   * The following command will change the ownership of a file named samplefile to a new owner named root and group krishnaprasadkv:

`chown root:krishnaprasadkv samplefile`   

   * If you omit the group name after the colon (:) the group of the file is changed to the specified user’s login group:

`chown root: samplefile`


### Change the Group of a File

To change only the group of a file use the chown command followed by a colon (:) and the new group name (with no space between them) and the target file as an argument:

`chown :GROUP FILE`

* The following command will change the owning group of a file named samplefile to www-data:

`chown :www-data samplefile`

Another command that you can use to change the group ownership of files is [chgrp](https://linuxize.com/post/chgrp-command-in-linux/).

### Change Symbolic Links Ownership

When the recursive option is not used, chown command changes the group ownership of the files to which the symlinks points, not the symbolic links themselves.

For example, if you try to change the owner and the group of the symbolic link symlinkfile that points to /var/www/samplefile, chown will change the ownership of the file or directory the symlink points to:

`chown www-data: symlinkfile`

Chances are that instead of changing the target ownership, you will get a “cannot dereference ‘symlinkfile’: Permission denied” error.

The error occurs because by default on most Linux distributions symlinks are protected, and you cannot operate on target files. This option is specified in `/proc/sys/fs/protected_symlinks`. 1 means enabled and 0 disabled. We recommend not to disable the symlink protection.

To change the group ownership of the symlink itself, use the -h option:

`chown -h www-data symlinkfile`

### Recursively Change the File Ownership

To recursively operate on all files and directories under the given directory, use the -R (--recursive) option:


`chown -R USER:GROUP DIRECTORY`

The following example will change the ownership of all files and subdirectories under the /var/www directory to a new owner and group named www-data:

`chown -R www-data: /var/www`

If the directory contains symbolic links pass the -h option:

`chown -hR www-data: /var/www`  
Other options that can be used when recursively changing the directory ownership are -H and -L.  

If the argument passed to chown command is a symbolic link that points to a directory, the -H option will cause the command to traverse it. -L tells chown to traverse each symbolic link to a directory that is encountered. Usually, you should not use these options because you might mess up your system or create a security risk.  

### Using a Reference File  
The --reference=ref_file option allows you to change the user and group ownership of given files to be same as those of the specified reference file (ref_file). If the reference file is a symbolic link chown will use the user and group of the target file.  

`chown --reference=REF_FILE FILE`

For example, the following command will assign the user and group ownership of the samplefile to file2

`chown --reference=samplefile file2`


[soruce](https://linuxize.com/post/linux-chown-command/) 
