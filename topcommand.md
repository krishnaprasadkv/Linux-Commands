# Top Command

## Overview
When you need to see the running processes on your Linux in real time, you have top as your tool for that.  
Top also displays other information besides the running processes, like free memory both physical and swap also.  
 
## Top command explanation

* To monitor all processes in the system use the following command   
$ `top`
```
top - 14:13:05 up 0 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   4 total,   1 running,   3 sleeping,   0 stopped,   0 zombie
%Cpu(s): 30.1 us, 41.5 sy,  0.0 ni, 24.9 id,  0.0 wa,  3.6 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  1189172 free, 14817120 used,   236476 buff/cache
KiB Swap: 21265404 total, 20457076 free,   808328 used.  1284792 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0    8892    308    272 S   0.0  0.0   0:00.26 init
    7 root      20   0    8900    216    172 S   0.0  0.0   0:00.01 init
    8 krishna+  20   0   15104   3628   3532 S   0.0  0.0   0:00.33 bash
   22 krishna+  20   0   15912   1964   1400 R   0.0  0.0   0:00.01 top
``` 
* The first line in top  

`top - 14:14:15 up 1 min,  0 users,  load average: 0.52, 0.58, 0.59` 

“14:13:05″ is the current time; “up 1 day” shows how long the system has been up for; “0 user” how many users are logged in; “load average: 0.52, 0.58, 0.59″ the load average of the system (1minute, 5 minutes, 15 minutes). 

* The second line in top  

`Tasks:   4 total,   1 running,   3 sleeping,   0 stopped,   0 zombie`

Shows the number of processes and their current state. 

* The third line in top: 
`%Cpu(s): 30.1 us, 41.5 sy,  0.0 ni, 24.9 id,  0.0 wa,  3.6 hi,  0.0 si,  0.0 st`

Shows CPU utilization details. “30.1%us” user processes are using 9.5%; “41.5%sy” system processes are using 41.5%; “24.9%id” percentage of available cpu; “0.0%wa” time CPU is waiting for IO. 
 
* The fourth and fifth lines in top  
`KiB Mem : 16242768 total,  1189172 free, 14817120 used,   236476 buff/cache`
`KiB Swap: 21265404 total, 20457076 free,   808328 used.  1284792 avail Mem` 

“16242768k total” is total memory in the system; “14817120K used” is the part of the RAM that currently contains information; “1189172k free” is the part of RAM that contains no information; “1189172k buffers and 1284792k cached” is the buffered and cached data for IO. 
 
## Top command task's property
* By default, top starts by showing the following task's property  
 
|Field |Description|
|:--:| :--|
|PID |Process |
|ID |USER Effective User ID|
|PR |Dynamic priority| 
|NI |Nice value, also known as base priority |
|VIRT |Virtual Size of the task. This includes the size of process's executable binary, the data area and all the loaded shared libraries. |
|RES |The size of RAM currently consumed by the task. Swapped out portion of the task is not included. |
|SHR |Some memory areas could be shared between two or more task, this field reflects that shared areas. The example of shared area are shared library and SysV shared memory. S Task status| 
|%CPU |The percentage of CPU time dedicated to run the task since the last top's screen update.|
| %MEM |The percentage of RAM currently consumed by the task. |
|TIME+ |The total CPU time the task has been used since it started. "+" sign means it is displayed with hundredth of a second granularity. By default, TIME/TIME+ doesn't account the CPU time used by the task's dead children. |
|Command |Showing program names |
 
## Working with top command 

Now that we are able to understand the output from TOP lets learn how to change the way 
the output is displayed. Just press the following key while running top and the output will be sorted in real time. 

|Options| Description|
|:--:|:--|
| u | Display specific user process|
|d |change delay or set screen refresh interval|
| M |Sort by memory usage |
|P  | Sort by CPU usage |
|T | Sort by cumulative time|
|z | Color display |
|k | Kill a process | 
|q | quit |
|r | to renice a process |
| h | help |

* To kill the process with PID 40, then press “k” and a prompt will ask you for the PID number, and enter 40. When asked about signal number give 9 or 15.  
Note : [To learn about signal numbers](https://github.com/krishnaprasadkv/linux-commands/blob/master/signalsinlinux.md#few-important-signals-with-its-descriptions) 
 ```
 top - 16:48:19 up 6 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   7 total,   1 running,   6 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.7 us,  9.5 sy,  0.0 ni, 79.3 id,  0.0 wa,  0.4 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  7097544 free,  8908748 used,   236476 buff/cache
KiB Swap: 21265404 total, 21159464 free,   105940 used.  7193164 avail Mem
PID to signal/kill [default pid = 1] 40                                                                                            PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0    8892    304    268 S   0.0  0.0   0:00.12 init
    7 root      20   0    8900    212    168 S   0.0  0.0   0:00.00 init
    8 krishna+  20   0   15104   3608   3516 S   0.0  0.0   0:00.20 bash
   23 root      20   0    8900    216    172 S   0.0  0.0   0:00.01 init
   24 krishna+  20   0   15104   3616   3524 S   0.0  0.0   0:00.12 bash
   40 krishna+  20   0   12196    784    540 S   0.0  0.0   0:00.00 cat
   41 krishna+  20   0   15912   1900   1336 R   0.0  0.0   0:00.01 top
                                                                           
top - 16:48:19 up 6 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   7 total,   1 running,   6 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.7 us,  9.5 sy,  0.0 ni, 79.3 id,  0.0 wa,  0.4 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  7097544 free,  8908748 used,   236476 buff/cache
KiB Swap: 21265404 total, 21159464 free,   105940 used.  7193164 avail Mem
Send pid 44 signal [15/sigterm] 9                                                                                             PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0    8892    304    268 S   0.0  0.0   0:00.12 init
    7 root      20   0    8900    212    168 S   0.0  0.0   0:00.00 init
    8 krishna+  20   0   15104   3608   3516 S   0.0  0.0   0:00.20 bash
   23 root      20   0    8900    216    172 S   0.0  0.0   0:00.01 init
   24 krishna+  20   0   15104   3616   3524 S   0.0  0.0   0:00.12 bash
   40 krishna+  20   0   12196    784    540 S   0.0  0.0   0:00.00 cat
   41 krishna+  20   0   15912   1900   1336 R   0.0  0.0   0:00.01 top             
 ```

* Display specific user process. using top command with `-u` option will display specific users process details.

$`top -u krishnaprasadkv`
```
top - 17:09:54 up 27 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.8 us,  9.0 sy,  0.0 ni, 79.7 id,  0.0 wa,  0.5 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  7342616 free,  8663676 used,   236476 buff/cache
KiB Swap: 21265404 total, 21100212 free,   165192 used.  7438236 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
   45 krishna+  20   0   15920   1916   1348 R 100.0  0.0   0:00.06 top
    8 krishna+  20   0   15104   3600   3500 S   0.0  0.0   0:00.21 bash
   24 krishna+  20   0   15104   3612   3424 S   0.0  0.0   0:00.13 bash
```

* Change delay or set screen refresh interval in top. By default screen refresh interval is 3.0 seconds, same can be change pressing `d` option in running top command and change it as desired as shown below

```
top - 17:19:41 up 37 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
%Cpu(s): 13.1 us, 13.5 sy,  0.0 ni, 73.1 id,  0.0 wa,  0.3 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  7471712 free,  8534580 used,   236476 buff/cache
KiB Swap: 21265404 total, 21098532 free,   166872 used.  7567332 avail Mem
Change delay from 3.0 to 2                                                                                             PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
   45 krishna+  20   0   15920   1980   1412 R   0.5  0.0   0:01.34 top
    8 krishna+  20   0   15104   3600   3500 S   0.0  0.0   0:00.21 bash
   24 krishna+  20   0   15104   3612   3424 S   0.0  0.0   0:00.13 bash
``` 

* Highlight running process. Press `z` option in running top command will display running process in color which may help you to identified running process easily.

```
Tasks:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
%Cpu(s):  8.6 us, 10.8 sy,  0.0 ni, 80.4 id,  0.0 wa,  0.2 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  7525756 free,  8480536 used,   236476 buff/cache
KiB Swap: 21265404 total, 21100312 free,   165092 used.  7621376 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
   45 krishna+  20   0   15920   2004   1436 R   0.5  0.0   0:02.00 top
    8 krishna+  20   0   15104   3600   3500 S   0.0  0.0   0:00.21 bash
   24 krishna+  20   0   15104   3612   3424 S   0.0  0.0   0:00.13 bash
```
* Save top command results. To save the running top command results output to a file.

$ `top -n 1 -b > top-output.txt`
```
Krishnaprasadkv:~$ top -n 1 -b >top-output.txt
krishnaprasadkv:~$ cat top-output.txt
top - 17:26:19 up 44 min,  0 users,  load average: 0.52, 0.58, 0.59
Tasks:   7 total,   1 running,   6 sleeping,   0 stopped,   0 zombie
%Cpu(s): 11.6 us,  8.7 sy,  0.0 ni, 79.2 id,  0.0 wa,  0.5 hi,  0.0 si,  0.0 st
KiB Mem : 16242768 total,  7679060 free,  8327232 used,   236476 buff/cache
KiB Swap: 21265404 total, 21100520 free,   164884 used.  7774680 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0    8892    300    264 S   0.0  0.0   0:00.12 init
    7 root      20   0    8900    212    168 S   0.0  0.0   0:00.00 init
    8 krishna+  20   0   15104   3596   3496 S   0.0  0.0   0:00.21 bash
   23 root      20   0    8900    216    172 S   0.0  0.0   0:00.01 init
   24 krishna+  20   0   15104   3616   3504 S   0.0  0.0   0:00.20 bash
   45 krishna+  20   0   15920   2000   1432 S   0.0  0.0   0:02.85 top
   48 krishna+  20   0   15768   1796   1324 R   0.0  0.0   0:00.01 top
```
* Getting top command help. By pressing `h` to obtain top command help.
```
Help for Interactive Commands - procps-ng version 3.3.10
Window 1:Def: Cumulative mode Off.  System: Delay 3.0 secs; Secure mode Off.

  Z,B,E,e   Global: 'Z' colors; 'B' bold; 'E'/'e' summary/task memory scale
  l,t,m     Toggle Summary: 'l' load avg; 't' task/cpu stats; 'm' memory info
  0,1,2,3,I Toggle: '0' zeros; '1/2/3' cpus or numa node views; 'I' Irix mode
  f,F,X     Fields: 'f'/'F' add/remove/order/sort; 'X' increase fixed-width

  L,&,<,> . Locate: 'L'/'&' find/again; Move sort column: '<'/'>' left/right
  R,H,V,J . Toggle: 'R' Sort; 'H' Threads; 'V' Forest view; 'J' Num justify
  c,i,S,j . Toggle: 'c' Cmd name/line; 'i' Idle; 'S' Time; 'j' Str justify
  x,y     . Toggle highlights: 'x' sort field; 'y' running tasks
  z,b     . Toggle: 'z' color/mono; 'b' bold/reverse (only if 'x' or 'y')
  u,U,o,O . Filter by: 'u'/'U' effective/any user; 'o'/'O' other criteria
  n,#,^O  . Set: 'n'/'#' max tasks displayed; Show: Ctrl+'O' other filter(s)
  C,...   . Toggle scroll coordinates msg for: up,down,left,right,home,end

  k,r       Manipulate tasks: 'k' kill; 'r' renice
  d or s    Set update interval
  W,Y       Write configuration file 'W'; Inspect other output 'Y'
  q         Quit
          ( commands shown with '.' require a visible task display window )
Press 'h' or '?' for help with Windows,
Type 'q' or <Esc> to continue            
```