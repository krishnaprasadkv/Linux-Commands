# Linux Links

* A link in UNIX is a pointer to a file. Like pointers in any programming languages, links in UNIX are pointers pointing to a file or a directory. Creating links is a kind of shortcuts to access a file. Links allow more than one file name to refer to the same file, elsewhere.

### Types of Links:

    * Soft Link or Symbolic links
    * Hard Links

### Types of Files:

| Symbol | Type of File |
| :--: | :-- |
| - |Normal file |
| d |Directory|
| l |Link file (shortcut) |
| b |Block file (Harddisk, Floppy disk) |
| c |Character file (Keyboard, Mouse) |
 
### Difference between soft link and hard link:  

| Soft Link | Hard link|
| :--| :--|
| Size of link file is equal to no. of characters in the name of original file| Size of both file is same|
|Can be created across the Partition| Can't be created across the partition |
|Inode no. of source and link file is different| Inode no. of both file is same |
| if original file is deleted, link is broken and data is lost| If original file is deleted then also link will contain data |
|SHORTCUT FILE| BACKUP FILE |
|`ln -s <source> <linkname>` | `ln <source> <linkname>`|
 
### Working with Links: 

* Creating a soft link   
$ `ln -s samplefile samplefile.slink`
```
$ ln -s samplefile samplefile.slink
$ ls -l
total 0
drwxrwxrwx 1 root krishnaprasadkv 4096 May 27 14:45 sampledir
-rwxrwxrwx 1 root krishnaprasadkv  139 May 30 14:30 samplefile
lrwxrwxrwx 1 root root              10 May 30 15:14 samplefile.slink -> samplefile 
``` 

* Creating a Hard link  
$ `ln testing testing.hlink`

```
$ ln testing testing.hlink
$ ls -l
total 0
drwxrwxrwx 1 root krishnaprasadkv 4096 May 27 14:45 sampledir
-rwxrwxrwx 1 root krishnaprasadkv  139 May 30 14:30 samplefile
lrwxrwxrwx 1 root root              10 May 30 15:14 samplefile.slink -> samplefile
-rw-r--r-- 2 root root               0 May 30 15:16 testing
-rw-r--r-- 2 root root               0 May 30 15:16 testing.hlink
```

* List help page of ln command with their option.  
$ `ln --help`

```
Usage: ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
  or:  ln [OPTION]... TARGET                  (2nd form)
  or:  ln [OPTION]... TARGET... DIRECTORY     (3rd form)
  or:  ln [OPTION]... -t DIRECTORY TARGET...  (4th form)
In the 1st form, create a link to TARGET with the name LINK_NAME.
In the 2nd form, create a link to TARGET in the current directory.
In the 3rd and 4th forms, create links to each TARGET in DIRECTORY.
Create hard links by default, symbolic links with --symbolic.
By default, each destination (name of new link) should not already exist.
When creating hard links, each TARGET must exist.  Symbolic links
can hold arbitrary text; if later resolved, a relative link is
interpreted in relation to its parent directory.

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL]      make a backup of each existing destination file
  -b                          like --backup but does not accept an argument
  -d, -F, --directory         allow the superuser to attempt to hard link
                                directories (note: will probably fail due to
                                system restrictions, even for the superuser)
  -f, --force                 remove existing destination files
  -i, --interactive           prompt whether to remove destinations
  -L, --logical               dereference TARGETs that are symbolic links
  -n, --no-dereference        treat LINK_NAME as a normal file if
                                it is a symbolic link to a directory
  -P, --physical              make hard links directly to symbolic links
  -r, --relative              create symbolic links relative to link location
  -s, --symbolic              make symbolic links instead of hard links
  -S, --suffix=SUFFIX         override the usual backup suffix
  -t, --target-directory=DIRECTORY  specify the DIRECTORY in which to create
                                the links
  -T, --no-target-directory   treat LINK_NAME as a normal file always
  -v, --verbose               print name of each linked file
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is '~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Using -s ignores -L and -P.  Otherwise, the last option specified controls
behavior when a TARGET is a symbolic link, defaulting to -P.
```
