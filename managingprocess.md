# MANAGING PROCESS 
 
## Overview   

A Linux process is a program running in the Linux system. Depending on Linux distributions, it's also known as service. A Linux process is called daemon. 

When you start a program or running an application in Linux, you actually execute that program. A Linux process (a daemon), running in foreground or in the background, uses memory and CPU resources. That's why we need to manage Linux process. Keeping unused Linux process running in the system is a waste and also exposes your system to security threat. 
 
In Linux, every running process or daemon is given an identity number called PID (Process ID). The process id is unique. We can terminate unused program in the system by stopping its process id. 
 
In order to manage Linux processes, we need to identify some process information such as who's responsible for the process, which terminal the process is running from and what command used to run the process. 
 
## Types of processes   
 
    * Interactive Processes 
    * System Process or Daemon 
    * Automatic or batch 
 
### Interactive Processes 
Interactive processes are those processes that are invoked by a user and can interact with the user. VI is an example of an interactive process. Interactive processes can be classified into foreground and background processes. The foreground process is the process that you are currently interacting with, and is using the terminal as its stdin (standard input) and stdout (standard output). A background process is not interacting with the user and can be in one of two states - paused or running.  
 
### System Process or Daemon
Daemon is the term used to refer to processes that are running on the computer and provide services but do not interact with the console. Most server software is implemented as a daemon. Example are Apache, Samba. 

Any process can become a daemon as long as it is run in the background, and does not interact with the user. A simple example of this can be achieved using the [ls -R] command. This will list all subdirectories on the computer, and is similar to the [dir /s] command on Windows. This command can be set to run in the background by typing [ls -R &], and although technically you have control over the shell prompt, you will be able to do little work as the screen displays the output of the process that you have running in the background. You will also notice that the standard pause (ctrl+z) and kill (ctrl+c) commands do little to help you.  
 
### Automatic Processes  
Automatic processes are not connected to a terminal. Rather, these are tasks that can be queued into a spooler area, where they wait to be executed on a FIFO (first-in, first-out) basis. Such tasks can be executed using one of two criteria:    
At certain date and time: done using the “at “command   
At times when the total system load is low enough to accept extra jobs: done using the Cron command. By default, tasks are put in a queue where they wait to be executed until the system load is lower than 0.8. In large environments, the system administrator may prefer cron job processing when large amounts of data have to be processed or when tasks demanding a lot of system resources have to be executed on an already loaded system. Cron job processing is also used for optimizing system performance. 

### Parent and Child Process 
The Process which starts or creates another process is called parent process and the one which got created is known as child process.     
Every process will be having a parent process except init process.      
The init process is the parent of all the process in the system. It is the first process   which gets started by the kernel at the time of booting.    
The PID of init will be 1.   
Only after init process gets started the remaining process are called by it, and hence it is responsible for all the remaining processes in the system.   


## Working with ps command

* To monitor the process using ps command 
    * The ps command gives the running process of the present terminal and present command.   
$ `ps `
```
$ ps
  PID TTY          TIME CMD
    8 tty1     00:00:00 bash
   22 tty1     00:00:00 ps
   
```

* To see total number of  processes running in the system  
$ `ps -a`  
```
$ ps -a
  PID TTY          TIME CMD
    8 tty1     00:00:00 bash
   23 tty1     00:00:00 ps
```

* To see the processes running by the logged in user    
$ `ps -u or ps -u <usrname>`
```
$ ps -u
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
krishna+     8  0.0  0.0  15096  3732 tty1     S    14:03   0:00 -bash
krishna+    26  0.0  0.0  15664  1848 tty1     R    14:08   0:00 ps -u
``` 

* To see which process are attached with some terminals (tty) and which are not   
$ `ps -x`
```
$ ps -x
  PID TTY      STAT   TIME COMMAND
    8 tty1     S      0:00 -bash
   28 tty1     R      0:00 ps -x
```

* To see which process are running by a particular group   
 $ `ps –G <group name> or $ pgrep –G <group name> `
 ```
 $ ps -G krishnaprasadkv
  PID TTY          TIME CMD
    8 tty1     00:00:00 bash
   31 tty1     00:00:00 ps
```
* To see the offline process of the system, already executed   
$ ` ps -aux`
```
$ ps -aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   8892   312 ?        Ssl  14:03   0:00 /init
root         7  0.0  0.0   8900   220 tty1     Ss   14:03   0:00 /init
krishna+     8  0.0  0.0  15096  3732 tty1     S    14:03   0:00 -bash
krishna+    32  0.0  0.0  15664  1860 tty1     R    14:16   0:00 ps -aux
```