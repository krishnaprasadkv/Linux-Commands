# Filter Commands

## Overview
Filter commands are used to filter the output so that the required things can easily be picked up. The commands which are used to filter the output are   
<b>
$ less  
$ more  
$ head  
$ tail  
$ sort  
$ cut  
$ sed  
</b>

### less:-

* The less command is used to see the output line wise or page wise.   
  Ex: $ `less /etc/passwd`

```
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
    uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin  
    proxy:x:13:13:proxy:/bin:/usr/sbin/nologin  
```

  Note: -press Enter key to scroll down line by line (or)  
  Use d to go to next page  
  Use b to go to previous page  
  Use / to search for a word in the file 
  Use v to go vi mode where you can edit the file and once you save it you will back to less command

### more:- 
* More is exactly same like less  
  Ex: $ `more /etc/passwd` 

  Note: -press Enter key to scroll down line by line (or)  
  Use d to go to next page  
  Use / to search for a word in the file 
  Use v to go vi mode where you can edit the file and once you save it you will back to more command 
 
### head:-
* It is used to display the top 10 lines of the file.    
  Ex: $ `head /etc/passwd` 
```
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
* To display the custom lines #head -n /etc/passwd (where n can be any number).  
  Ex: $ `head -3 /etc/passwd` 
 ```
    root:x:0:0:root:/root:/bin/bash
    daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
    bin:x:2:2:bin:/bin:/usr/sbin/nologin
 ```
### tail:-
* It is used to display the last 10 lines of the file  
Ex: $ `tail /etc/passwd` 
``` 
    systemd-bus-proxy:x:103:105:systemd Bus Proxy,,,:/run/systemd:/bin/false  
    syslog:x:104:108::/home/syslog:/bin/false  
    _apt:x:105:65534::/nonexistent:/bin/false  
    lxd:x:106:65534::/var/lib/lxd/:/bin/false  
    messagebus:x:107:111::/var/run/dbus:/bin/false  
    uuidd:x:108:112::/run/uuidd:/bin/false  
    dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/bin/false  
    sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin  
    pollinate:x:111:1::/var/cache/pollinate:/bin/false  
    krishnaprasadkv:x:1000:1000:,,,:/home/krishnaprasadkv:/bin/bash  

``` 
* To display the custom lines   
Ex: $ `tail -3 /etc/passwd` 
```
    sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin  
    pollinate:x:111:1::/var/cache/pollinate:/bin/false  
    krishnaprasadkv:x:1000:1000:,,,:/home/krishnaprasadkv:/bin/bash 
```
### Sort:-
* It is used to sort the output in numeric or alphabetic order. Syntax is `sort filename`

* sort by alphabetic order   
    * For testing purpose will use below file.

$  `cat sample.txt`
```
    welcome to CLI
    Linux basic commands
    Hello world
    testing
    scripts
    Hello world 
```
$ `sort sample.txt`
```
    Hello world
    Hello world
    Linux basic commands
    scripts
    testing
    welcome to CLI
```
* To sort the file according to numbers 
Ex: $ `sort –d sample.txt`
```
    1. Linux basic commands
    2. scripts
    3. Hello world
    4. welcome to CLI
    5. Hello world
    6. testing
``` 

* To remove the duplicate entries from the output.  
Ex: $ `sort –u sample.txt`
```
    Hello world
    Linux basic commands
    scripts
    testing
    welcome to CLI
``` 

### cut:-
* The cut command is used to pick the given expression (in columns) and display the output.  
$ `cut  -d  -f   filename` (where d stands for delimiter ex. : , “  “ etc and f stands for field)   
* To delimit colon(:) and print the field 
Ex: $ `cut -d: -f1  /etc/passwd`
```
    root
    daemon
    bin
    sys
    sync
    games
    man
    lp
    mail
``` 
To delimit spaces and print the field  
Ex: $ `cut –d “ “ –f1 sample.txt`  
```
    welcome
    Linux
    Hello
    testing
    scripts
    Hello
``` 
### sed:-
* sed stands for stream editor, which is used to search a word in the file and replace it with the word required to be in the output  

$ `sed  ‘s/searchfor/replacewith/g’  filename`   
Note: it will only modify the output, but there will be no change in the original file.

Ex: $ `sed 's/Hello/hai/g' sample.txt`

```
    welcome to CLI
    Linux basic commands
    hai world
    testing
    scripts
    hai world
```

* List help page of filter command with their option.   

$ `less --help`
$ `more --help` 
$ `head --help`   
$ `tail --help`   
$ `sort --help`   
$ `cut --help`   
$ `sed --help` 