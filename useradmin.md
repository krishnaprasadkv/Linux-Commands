# USER ADMINISTRATION 

## Overview 
In Linux/Unix user is one who uses the system. There can be at least one or more than one users in Linux at a time. Users on a system are identified by a username and a userid. The username is something that users would normally refer to, but as far as the operating system is concerned this is referred to using the user id (or uid). The username is typically a user friendly string, such as your name, whereas the user id is a number. The words username and userid are often (incorrectly) used interchangeably. The user id numbers should be unique (one number per user). If you had two usernames with the same user id, effectively there permissions would be the same and the files that they create would appear to have been created by the same user. This should not be allowed and the useradd command will not allow usernames to share the same userid.   
 
### Some Important Points related to Users
* Users and groups are used to control access to files and resources.
* Users login to the system by supplying their username and password.
* Every file on the system is owned by a user and associated with a group.
* Every process has an owner and group affiliation, and can only access the resources its owner or group can access. 
* Every user of the system is assigned a unique user ID number ( the UID). 
* Users name and UID are stored in __/etc/passwd__.
* User’s password is stored in __/etc/shadow__ in encrypted form. 
* Users are assigned a home directory and a program that is run when they login (Usually a shell) 
* Users cannot read, write or execute each other’s files without permission. 
 
## Types of Users In Linux
 
|TYPE| EXAMPLE| USER ID (UID)| GROUP ID (GID) |HOME DIRECTORY |SHELL |
|:--:|:--|:--:|:--:|:--|:--|
|Super user |Root| 0| 0 |/root| /bin/bash |
|System user |ftp, ssh, apache nobody |1 to 499 |1 to 499| /var/ftp , etc| /sbin/nologin |
|Normal user| Visitor, linux2,etc |500 to 60000 |500 to 60000 |/home/user name |/bin/bash |


### In Linux there are three types of users. 
 
1. **Super user or root user**  
Super user or the root user is the most powerful user. He is the administrator user.  
 
2. **System user**  
System users are the users created by the softwares or applications. For example if we install Apache it will create a user apache. These kinds of users are known as system users. 
 
3. **Normal user**  
Normal users are the users created by root user. They are normal users like __krishnaprasadkv__, Musab etc. Only the root user has the permission to create or remove a user. 
 
### Whenever a user is created in Linux things created by default 
* A home directory is created(/home/username)
* A mail box is created(/var/spool/mail) 
* unique __UID & GID__ are given to user 
 
### Linux uses UPG (User Private Group) scheme 
* It means that whenever a user is created is has its own private group
* For Example if a user is created with the name __krishnaprasadkv__, then a primary group for that user will be __krishnaprasadkv__ only 
 
### There are two important files a user administrator should be aware of.  
 
1. "/etc/passwd" 
2. "/etc/shadow" 
 
### Each of the above mentioned files have specific formats. 
 
1. `/etc/passwd` 
```
krishnaprasadkv@DESKTOP-JDIP4H0:~# head /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
```
* The above fields are 
    * __root__ =name 
    * __x__ = link to password file i.e. /etc/shadow 
    * __0 or 1__ = UID (user id) 
    * __0 or 1__ =GID (group id) 
    * __root or bin__ = comment (brief information about the user) 
    * __/root or /bin__ = home directory of the user 
    * __/bin/bash or /sbin/nologin__ = shell  

2. `/etc/shadow` 
 
`krishnaprasadkv:#6#LpCnJk2Y#Jwuy4kofRZN4pzOuIM0aNtk7FYody1b/oZLPZ2JGPkoIHrkWIVt1YqzU7vrlGNN6neJBW37rdLRYBPhcFImDS/:18061:0:99999:7:::`

* The fields are as follows, 
    * __krishnaprasadkv__ = User name 
    * __:#6#LpCnJk2Y#Jwuy4kofRZN4pzOuIM0aNtk7FYody1b/oZLPZ2JGPkoIHrkWIVt1YqzU7vrlGNN6neJBW37rdLRYBPhcFImDS__ = Encrypted password 
    * __18061__ = Days since that password was last changed.
    * __0__ = Days after which password must be changed. 
    * __99999__ = Days before password is to expire that user is warned. 
    * __7__ = Days after the password is expires that the user is disabled.
    * A reserved field. 
 
### Password Complexity Requirements: 
 
* A root user can change password of self and of any user in the system, there are no rules for root to assign a password. Root can assign any length of password either long or short, it can be alphabet or numeric or both. On the whole there is no limitation for root for assigning a password. 
* A normal user can change only its password. Valid password for a normal user should adhere to the following rules 
* It should be at least __7__ characters but not more than 255 characters. 
* At least one character should be __Upper case__
* At least one character should be __Lower case__
* At least one character should be a __symbol__, and one character should be a __number__. 
* It should not match the previous password. 
* It cannot have a sequence (__ex: 123456 or abcdef__ ) 
* The __login name__ and the __password__ cannot be same.   

**Note:** For security reasons don’t keep the password based on __date of birth__ because it can easily be hacked. 

## Working with User Administration Commands

## Creating a User 
* The syntax for creating a user in Linux is   
    `# useradd  <option>  <username>`    
* options are 
    * `-u` user id 
    * `-G` Secondary group id 
    * `-g` primary group id
    * `-d` home directory 
    * `-c` comment 
    * `-s` shell 

### Let’s create a user with default attributes. 
 
* When no option is used with `useradd` command the options like __UID, GID, home dir__ and __shell__ will be assigned default.  
`# useradd <username>`   
`# useradd linux `
```
~# useradd linux
root@DESKTOP-JDIP4H0:~# tail /etc/passwd
syslog:x:104:108::/home/syslog:/bin/false
_apt:x:105:65534::/nonexistent:/bin/false
lxd:x:106:65534::/var/lib/lxd/:/bin/false
messagebus:x:107:111::/var/run/dbus:/bin/false
uuidd:x:108:112::/run/uuidd:/bin/false
dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/bin/false
sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
krishnaprasadkv:x:1000:1000:,,,:/home/krishnaprasadkv:/bin/bash
linux:x:1001:1001::/home/linux:
root@DESKTOP-JDIP4H0:~#
```
* Observe that the __uid, gid, home dir,__ and __shell__ is assigned automatically. 
 
### Let’s create a user with our own attributes 
 
* Create a user with following attributes  
    * __Name__ = linux2   
    * __uid__ = 505  
    * __home dir__ = /home/linux2  
    * __comment__ =devops  

`# useradd linux2 -u 506 -d /home/linux2 -c devops`

```
root@DESKTOP-JDIP4H0:~# useradd linux2 -u 506 -d /home/linux2 -c devops
root@DESKTOP-JDIP4H0:~# tail /etc/passwd
_apt:x:105:65534::/nonexistent:/bin/false
lxd:x:106:65534::/var/lib/lxd/:/bin/false
messagebus:x:107:111::/var/run/dbus:/bin/false
uuidd:x:108:112::/run/uuidd:/bin/false
dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/bin/false
sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
krishnaprasadkv:x:1000:1000:,,,:/home/krishnaprasadkv:/bin/bash
linux:x:1001:1001::/home/linux:
linux2:x:506:1003:devops:/home/linux2:
``` 

## Assigning Password To The User 
 
* As a root user we can assign any password to any user 
* The syntax for assigning a password is `# passwd <user name>`
* `# passwd` to assign password to current user ( the one with which you have logged in, if it is root then root’s password will be changed) 
* `# passwd <user name>` to assign a password to a specific user, only root can assign password to other user.   

`# passwd linux2` 
```
root@DESKTOP-JDIP4H0:~# passwd linux2
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@DESKTOP-JDIP4H0:~#
``` 

## Modifying the User’s Attribute 
 
* After creating a user if we need to modify the attributes of user like changing uid, changing secondary group id or adding a comment, locking or unlocking the user account, can be done by following command 
* Syntax. `# usermod  <options>  <username>`
* options are: 
    * all the options which are used with useradd command can be used and also the following, 
    * `-l`  to change login name 
    * `-L`  to LOCK account 
    * `-U`  to UNLOCK account 
* ex. `# usermod -l newname oldname` Changing  the name of the  user
* ex. `# usermod -L newname`  To lock the user account 
* ex. `# usermod -U newname` To unlock the user account 

**Note:** - when an account is locked it will show! (Exclamation mark) in /etc/shadow file. 
 
## Locking and Unlocking a User Account 

### Locking User Account

* To lock a user account use the following 
* `# usermod –L < user name>`
* `# usermod –L  linux2`
* Verify it in `/etc/shadow` file, it shows exclamation mark before user account or try login as linux2 
```
root@DESKTOP-JDIP4H0:~# usermod -L linux2
root@DESKTOP-JDIP4H0:~# tail /etc/shadow
_apt:*:18037:0:99999:7:::
lxd:*:18037:0:99999:7:::
messagebus:*:18037:0:99999:7:::
uuidd:*:18037:0:99999:7:::
dnsmasq:*:18037:0:99999:7:::
sshd:*:18037:0:99999:7:::
pollinate:*:18037:0:99999:7:::
krishnaprasadkv:$6$LpCnJk2Y$Jwuy4kofRZN4pzOuIM0aNtk7FYody1b/oZLPZ2JGPkoIHrkWIVt1YqzU7vrlGNN6neJBW37rdLRYBPhcFImDS/:18061:0:99999:7:::
linux::18436:0:99999:7:::
linux2:!$6$4.zpS9u9$sHydkg99ujEal6ZV/9no0ww6I8Uh3hKTAND/NTPjM87.1v0vthID03xDLEAdf5PW16bdaxcx58crVJz.QT0o3/:18436:0:99999:7:::
root@DESKTOP-JDIP4H0:~# tail /etc/shadow
```

### Unlocking a user account: 
* Unlock the above account 
* `# usermod –U < user name >`
* `# usermod –U linux2`
* Verify it in /etc/shadow file, it shows exclamation mark before user account or try login as linux2 
```
root@DESKTOP-JDIP4H0:~# usermod -U linux2
root@DESKTOP-JDIP4H0:~# tail /etc/shadow
_apt:*:18037:0:99999:7:::
lxd:*:18037:0:99999:7:::
messagebus:*:18037:0:99999:7:::
uuidd:*:18037:0:99999:7:::
dnsmasq:*:18037:0:99999:7:::
sshd:*:18037:0:99999:7:::
pollinate:*:18037:0:99999:7:::
krishnaprasadkv:$6$LpCnJk2Y$Jwuy4kofRZN4pzOuIM0aNtk7FYody1b/oZLPZ2JGPkoIHrkWIVt1YqzU7vrlGNN6neJBW37rdLRYBPhcFImDS/:18061:0:99999:7:::
linux::18436:0:99999:7:::
linux2:$6$4.zpS9u9$sHydkg99ujEal6ZV/9no0ww6I8Uh3hKTAND/NTPjM87.1v0vthID03xDLEAdf5PW16bdaxcx58crVJz.QT0o3/:18436:0:99999:7:::
```
* Observe in both outputs that once the account is unlocked the exclamation is gone. 

##  Changing the Password Parameters
### Password Parameters 
* For any user we can set the parameters for the password, like min and max password age, password expiration warnings and account expiration date etc. 
* To view the advanced parameters of the user, use  
 
`# chage  -l < user name> `  
`# chage -l linux2`
 ```
root@DESKTOP-JDIP4H0:~# chage -l linux2
Last password change                                    : Jun 23, 2020
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
root@DESKTOP-JDIP4H0:~#
 ```
 
* __Last password change:__ When the password was change last time. 
* __Password expires:__ Password expiry date.
* __Password inactive:__ After password expiry grace period before the account gets locked. 
* __Account expires:__ Date on which the account expires. 
* __Minimum number of days b/w password change:__ once the password is changed, it cannot be changed until a min period of specified date. [0] means never. 
* __Max number of days b/w password change:__ After changing the password how long it will be valid for. 
* __Number of days of warning before password expires:__ start of warnings to change the password, no. of days before the password expires. 

### Changing the password parameters:  
* Changing of the password parameters can be done by two ways. 
1. #`chage  <user name >`
2. #`chage  <option> <value> <username>` 
 
* Let’s see the first method and then the other. 
* To set the password parameters of a user __linux2__ to  
    * **Min password age :** 2 days 
    * **Max password age:** 7 days 
    * **Password expiration warnings:** 2 days before password expires 
    * **Password inactive [-1]:** 0 same day account is locked after password expiry. 
    * **Account expiration date:**  2090-12-99 (dec 31st 2099)  

`# chage linux2 `
 
 ```
 root@DESKTOP-JDIP4H0:~# chage  linux2
Changing the aging information for linux2
Enter the new value, or press ENTER for the default

        Minimum Password Age [0]: 2
        Maximum Password Age [99999]: 7
        Last Password Change (YYYY-MM-DD) [2020-06-23]:
        Password Expiration Warning [7]: 2
        Password Inactive [-1]: 0
        Account Expiration Date (YYYY-MM-DD) [-1]: 2099-12-31
root@DESKTOP-JDIP4H0:~# chage -l linux2
Last password change                                    : Jun 23, 2020
Password expires                                        : Jun 30, 2020
Password inactive                                       : Jun 30, 2020
Account expires                                         : Dec 31, 2099
Minimum number of days between password change          : 2
Maximum number of days between password change          : 7
Number of days of warning before password expires       : 2
root@DESKTOP-JDIP4H0:~#
 ```
 
* The second method is for, if you want to change a particular field of password aging policy 
* #`chage <option> <value> <username>`
* The options which can be used are as follows 
    * `-m`  for Min password age  
    * `-M` for Max password age 
    * `-d` for last time the password is changed. 
    * `-W` Password expiration warnings 
    * `-I` Password inactive [-1 means inactive]. 
    * `-E` Account expiration date 
* Let’s see how to change only the account expiration date 
 ```
root@DESKTOP-JDIP4H0:~# chage -E 2090-12-31 linux2
root@DESKTOP-JDIP4H0:~# chage -l linux2
Last password change                                    : Jun 23, 2020
Password expires                                        : Jun 30, 2020
Password inactive                                       : Jun 30, 2020
Account expires                                         : Dec 31, 2090
Minimum number of days between password change          : 2
Maximum number of days between password change          : 7
Number of days of warning before password expires       : 2
 ```
 
* Likewise you can use any option listed above and change any particular field in password aging parameters. 

## Deleting a User 
* To delete a user the syntax used is  
`# userdel <username>`it will only delete the user but home directory will be there. To delete the user with its home directory use the following command. 
* #`userdel –r < user name >`
* #`userdel –r linux2 `
```
root@DESKTOP-JDIP4H0:~# userdel -r linux2
root@DESKTOP-JDIP4H0:~# tail /etc/passwd
syslog:x:104:108::/home/syslog:/bin/false
_apt:x:105:65534::/nonexistent:/bin/false
lxd:x:106:65534::/var/lib/lxd/:/bin/false
messagebus:x:107:111::/var/run/dbus:/bin/false
uuidd:x:108:112::/run/uuidd:/bin/false
dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/bin/false
sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
krishnaprasadkv:x:1000:1000:,,,:/home/krishnaprasadkv:/bin/bash
linux:x:1001:1001::/home/linux:
root@DESKTOP-JDIP4H0:~#
```

### List help page of useradd command with their option.
`# useradd --help`
```
root@DESKTOP-JDIP4H0:~# useradd --help
Usage: useradd [options] LOGIN
       useradd -D
       useradd -D [options]

Options:
  -b, --base-dir BASE_DIR       base directory for the home directory of the
                                new account
  -c, --comment COMMENT         GECOS field of the new account
  -d, --home-dir HOME_DIR       home directory of the new account
  -D, --defaults                print or change default useradd configuration
  -e, --expiredate EXPIRE_DATE  expiration date of the new account
  -f, --inactive INACTIVE       password inactivity period of the new account
  -g, --gid GROUP               name or ID of the primary group of the new
                                account
  -G, --groups GROUPS           list of supplementary groups of the new
                                account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           use this alternative skeleton directory
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -l, --no-log-init             do not add the user to the lastlog and
                                faillog databases
  -m, --create-home             create the user's home directory
  -M, --no-create-home          do not create the user's home directory
  -N, --no-user-group           do not create a group with the same name as
                                the user
  -o, --non-unique              allow to create users with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       encrypted password of the new account
  -r, --system                  create a system account
  -R, --root CHROOT_DIR         directory to chroot into
  -s, --shell SHELL             login shell of the new account
  -u, --uid UID                 user ID of the new account
  -U, --user-group              create a group with the same name as the user
  -Z, --selinux-user SEUSER     use a specific SEUSER for the SELinux user mapping
      --extrausers              Use the extra users database

```
### List help page of usermod command with their option.
`usermod --help`
```
root@DESKTOP-JDIP4H0:~# usermod --help
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -a, --append                  append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                him/her from other groups
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the
                                new location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -R, --root CHROOT_DIR         directory to chroot into
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
  -v, --add-subuids FIRST-LAST  add range of subordinate uids
  -V, --del-subuids FIRST-LAST  remove range of subordinate uids
  -w, --add-subgids FIRST-LAST  add range of subordinate gids
  -W, --del-subgids FIRST-LAST  remove range of subordinate gids
  -Z, --selinux-user SEUSER     new SELinux user mapping for the user account

root@DESKTOP-JDIP4H0:~#
``` 

### List help page of chage command with their option.
`# chage --help` 
```
root@DESKTOP-JDIP4H0:~# chage --help
Usage: chage [options] LOGIN

Options:
  -d, --lastday LAST_DAY        set date of last password change to LAST_DAY
  -E, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -h, --help                    display this help message and exit
  -I, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -l, --list                    show account aging information
  -m, --mindays MIN_DAYS        set minimum number of days before password
                                change to MIN_DAYS
  -M, --maxdays MAX_DAYS        set maximim number of days before password
                                change to MAX_DAYS
  -R, --root CHROOT_DIR         directory to chroot into
  -W, --warndays WARN_DAYS      set expiration warning days to WARN_DAYS

root@DESKTOP-JDIP4H0:~#
```
### List help page of userdel command with their option.
`# userdel --help` 
```
root@DESKTOP-JDIP4H0:~# userdel --help
Usage: userdel [options] LOGIN

Options:
  -f, --force                   force removal of files,
                                even if not owned by user
  -h, --help                    display this help message and exit
  -r, --remove                  remove home directory and mail spool
  -R, --root CHROOT_DIR         directory to chroot into
      --extrausers              Use the extra users database
  -Z, --selinux-user            remove any SELinux user mapping for the user

root@DESKTOP-JDIP4H0:~#
```
### List help page of passwd command with their option.
`# passwd --help`
```
root@DESKTOP-JDIP4H0:~# passwd --help
Usage: passwd [options] [LOGIN]

Options:
  -a, --all                     report password status on all accounts
  -d, --delete                  delete the password for the named account
  -e, --expire                  force expire the password for the named account
  -h, --help                    display this help message and exit
  -k, --keep-tokens             change password only if expired
  -i, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -l, --lock                    lock the password of the named account
  -n, --mindays MIN_DAYS        set minimum number of days before password
                                change to MIN_DAYS
  -q, --quiet                   quiet mode
  -r, --repository REPOSITORY   change password in REPOSITORY repository
  -R, --root CHROOT_DIR         directory to chroot into
  -S, --status                  report password status on the named account
  -u, --unlock                  unlock the password of the named account
  -w, --warndays WARN_DAYS      set expiration warning days to WARN_DAYS
  -x, --maxdays MAX_DAYS        set maximum number of days before password
                                change to MAX_DAYS

root@DESKTOP-JDIP4H0:~#
```