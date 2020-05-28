# Find Command:-
 
Find command is used to find the files or directory’s path, it is exactly like the find option in windows where you can search for a file. 
 
Syntax: `find / (under root) –option filename `
 
Options that can be used with find command: 
 
 | Option | Usage|
 | :---:| :--|
 | -name | For searching a file with its name |
 | -inum | For searching a file with particular inode number |
 | -type | For searching a particular type of file |
 | -user | For files whose owner is a particular user |
 | -group| For files belonging to particular group |
 
* Finding a File with name   
$ `$ find -name samplefile`

```
./krishna/samplefile
``` 

* Finding a file with its inode number     
$ `find / -inum 8444249301491656`   
Note: Use `ls -il` command to find inode value   
```
$ ls -il
total 0
10133099161755539 drwxrwxrwx 1 root krishnaprasadkv 4096 May 27 14:45 sampledir
 8444249301491656 -rwxrwxrwx 1 root krishnaprasadkv    0 May 27 14:45 samplefile
$ find -inum 8444249301491656
./krishna/samplefile
```
* Finding the files, whose owner is a user called krishnaprasadkv   
$ `find / -user krishnaprasadkv`   
```
/home/krishnaprasadkv/test/Technology  
/home/krishnaprasadkv/test/Technology/Cloud  
/home/krishnaprasadkv/test/Technology/Cloud/AWS  
/home/krishnaprasadkv/test/Technology/Cloud/Azure  
/home/krishnaprasadkv/test/Technology/Cloud/GCP  
/home/krishnaprasadkv/test/Technology/Devops  
/home/krishnaprasadkv/test/Technology/Devops/ansible  
/home/krishnaprasadkv/test/Technology/Devops/docker  
/home/krishnaprasadkv/test/Technology/Devops/kubernetes  
/home/krishnaprasadkv/test/Technology/test  
/home/krishnaprasadkv/test/–P  
/home/krishnaprasadkv/test.c  
/home/krishnaprasadkv/testing  
/home/krishnaprasadkv/testing/test.json  
```  
* Finding the files whose group is “ktgroup”   
$ `find / -group ktgroup`   
  ```
/home/krishnaprasadkv/test/Technology  
/home/krishnaprasadkv/test/Technology/Cloud  
/home/krishnaprasadkv/test/Technology/Cloud/AWS  
/home/krishnaprasadkv/test/Technology/Cloud/Azure  
/home/krishnaprasadkv/test/Technology/Cloud/GCP  
/home/krishnaprasadkv/test/Technology/Devops  
/home/krishnaprasadkv/test/Technology/Devops/ansible  
/home/krishnaprasadkv/test/Technology/Devops/docker  
/home/krishnaprasadkv/test/Technology/Devops/kubernetes  
/home/krishnaprasadkv/test/Technology/test  
/home/krishnaprasadkv/test/–P  
/home/krishnaprasadkv/test.c  
/home/krishnaprasadkv/testing  
/home/krishnaprasadkv/testing/test.json  
 ```
