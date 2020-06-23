# GROUP ADMINISTRATION 

## Overview
* Users are assigned to groups with unique group ID numbers (the GID). 
* The group name and GID are stored in /etc/group.  
* Each user is given their own private group. 
* They can also be added to their groups to gain additional access. 
* All users in a group can share files that belong to the group. 
* Each user is a member of at least one group, called a primary group. In addition, a user can be a member of an unlimited number of secondary groups. 
* Group membership can be used to control the files that a user can read and edit. 
* For example, if two users are working on the same project you might put them in the same group so they can edit a particular file that other users cannot access. 
* A user’s primary group is defined in the /etc/passwd file and Secondary groups are defined in the /etc/group file.
* The primary group is important because files created by this user will inherit that group affiliation. 
 
## Working with Group Administration Commands

## Creating a Group 

### Creating a Group with default options : 
* To create a group the syntax is    
`# groupadd  <name for the group>` 
`# groupadd linuxgrp`
```
root@DESKTOP-JDIP4H0:~# groupadd linuxgrp
root@DESKTOP-JDIP4H0:~# tail /etc/group
lxd:x:110:krishnaprasadkv
messagebus:x:111:
uuidd:x:112:
ssh:x:113:
mlocate:x:114:
admin:x:115:
krishnaprasadkv:x:1000:
docker:x:116:krishnaprasadkv
linux:x:1001:
linuxgrp:x:1002:
root@DESKTOP-JDIP4H0:~#
```
### Creating a group with user specified group id (GID)  
` # groupadd <option> <name for the group>`   
` # groupadd -g 556 linuxgrp2`  
* To verify it in `/etc/group`   
 ```
 root@DESKTOP-JDIP4H0:~# groupadd -g 556 linuxgrp2
root@DESKTOP-JDIP4H0:~# tail /etc/group
messagebus:x:111:
uuidd:x:112:
ssh:x:113:
mlocate:x:114:
admin:x:115:
krishnaprasadkv:x:1000:
docker:x:116:krishnaprasadkv
linux:x:1001:
linuxgrp:x:1002:
linuxgrp2:x:556:
root@DESKTOP-JDIP4H0:~#
 ```
 
## Modifying the properties of the group 

To modify the group properties the syntax is   
`# groupmod <option> <arguments> <group name>`  
* The options are 
    * `-g` to change the group id 
    * `-o` to override the previous assigned id, if it matches with the new one. 
    * `-n` to change the group name 
 
### Changing the GID of the group 
`# groupmod -g 555 linuxgrp2 `
* Verify it in /etc/group 
```
root@DESKTOP-JDIP4H0:~# groupmod -g 555 linuxgrp2
root@DESKTOP-JDIP4H0:~# tail /etc/group
messagebus:x:111:
uuidd:x:112:
ssh:x:113:
mlocate:x:114:
admin:x:115:
krishnaprasadkv:x:1000:
docker:x:116:krishnaprasadkv
linux:x:1001:
linuxgrp:x:1002:
linuxgrp2:x:555:
root@DESKTOP-JDIP4H0:~#
``` 
 
### Changing the name of the group 
* The syntax for changing the group name is  
` # groupmod –n <new name > < existing name > `
` # groupmod -n linuxgroup2 linuxgrp2` 
```
root@DESKTOP-JDIP4H0:~# groupmod -n linuxgroup2 linuxgrp2
root@DESKTOP-JDIP4H0:~# tail /etc/group
messagebus:x:111:
uuidd:x:112:
ssh:x:113:
mlocate:x:114:
admin:x:115:
krishnaprasadkv:x:1000:
docker:x:116:krishnaprasadkv
linux:x:1001:
linuxgrp:x:1002:
linuxgroup2:x:555:
root@DESKTOP-JDIP4H0:~#
``` 
 
## Adding and Removing Members to a Group 
* Adding the members to the group is to add users to the group. 
* To add the members to the group the syntaxes are 

### To add single user to the group 
   `# usermod –G <group name > < user name>`
   `# usermod -G linuxgroup2 linux2` 
```
root@DESKTOP-JDIP4H0:~# usermod -G linuxgroup2 linux2
root@DESKTOP-JDIP4H0:~# grep linuxgroup2 /etc/group
linuxgroup2:x:555:linux2
root@DESKTOP-JDIP4H0:~#
```

### Adding multiple users to the group with various attributes 
    `# gpasswd < option> <arguments> <group name>` 
    * Options: 
        * `-M` For Adding Multiple users to  a group 
        * `-A` For Adding a group Administrator 
        * `-a` For Adding a single user to a group 
        * `-d` Removing a user from a group 
    `# gpasswd –M <user>,<user>,<user> <group>` 
    `# gpasswd -M linux1,linux2,linux3,linux4,linux5 linuxgroup2`
```
root@DESKTOP-JDIP4H0:~# gpasswd -M linux1,linux2,linux3,linux4,linux5 linuxgroup2
root@DESKTOP-JDIP4H0:~# tail -10 /etc/group
krishnaprasadkv:x:1000:
docker:x:116:krishnaprasadkv
linux:x:1001:
linuxgrp:x:1002:
linuxgroup2:x:555:linux1,linux2,linux3,linux4,linux5
linux2:x:1003:
linux1:x:1004:
linux3:x:1005:
linux4:x:1006:
linux5:x:1007:
root@DESKTOP-JDIP4H0:~#
```
### Adding a single user using gpasswd 
`# gpasswd -a linux1 linuxgroup2` (verify it in /etc/group) 
```
root@DESKTOP-JDIP4H0:~# gpasswd -a linux1 linuxgroup2
Adding user linux1 to group linuxgroup2
root@DESKTOP-JDIP4H0:~# grep linuxgroup2 /etc/group
linuxgroup2:x:555:linux1,linux2,linux3,linux4,linux5
root@DESKTOP-JDIP4H0:~#
``` 
### Making a user as a administrator 
`# gpasswd -A linux1 linuxgroup2` (verify it in /etc/gshadow) 
```
root@DESKTOP-JDIP4H0:~# gpasswd -A linux1 linuxgroup2
root@DESKTOP-JDIP4H0:~# grep linuxgroup2 /etc/group
linuxgroup2:x:555:linux1,linux2,linux3,linux4,linux5
root@DESKTOP-JDIP4H0:~# 
``` 
### Removing a user from the group 
`# gpasswd -d linux2 linuxgroup2` 
```
root@DESKTOP-JDIP4H0:~# grep linuxgroup2 /etc/group
linuxgroup2:x:555:linux1,linux2,linux3,linux4,linux5
root@DESKTOP-JDIP4H0:~# gpasswd -d linux2 linuxgroup2
Removing user linux2 from group linuxgroup2
root@DESKTOP-JDIP4H0:~# grep linuxgroup2 /etc/group
linuxgroup2:x:555:linux1,linux3,linux4,linux5
root@DESKTOP-JDIP4H0:~# 
``` 
### To add and remove groups use can also use the graphical tool in linux 
`#system-config-users &`

### List help page of groupadd command with their option.
`# groupadd --help` 
```
root@DESKTOP-JDIP4H0:~# groupadd --help
Usage: groupadd [options] GROUP

Options:
  -f, --force                   exit successfully if the group already exists,
                                and cancel -g if the GID is already used
  -g, --gid GID                 use GID for the new group
  -h, --help                    display this help message and exit
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -o, --non-unique              allow to create groups with duplicate
                                (non-unique) GID
  -p, --password PASSWORD       use this encrypted password for the new group
  -r, --system                  create a system account
  -R, --root CHROOT_DIR         directory to chroot into
      --extrausers              Use the extra users database

```
### List help page of gpasswd command with their option.
`gpasswd --help`

```
root@DESKTOP-JDIP4H0:~# gpasswd --help
Usage: gpasswd [option] GROUP

Options:
  -a, --add USER                add USER to GROUP
  -d, --delete USER             remove USER from GROUP
  -h, --help                    display this help message and exit
  -Q, --root CHROOT_DIR         directory to chroot into
  -r, --remove-password         remove the GROUP's password
  -R, --restrict                restrict access to GROUP to its members
  -M, --members USER,...        set the list of members of GROUP
  -A, --administrators ADMIN,...
                                set the list of administrators for GROUP
Except for the -A and -M options, the options cannot be combined.
root@DESKTOP-JDIP4H0:~#
```