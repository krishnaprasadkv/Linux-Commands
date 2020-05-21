#### Creating a file in Linux:   
<b>cat (Concatenate)</b>: command is used to create a file and to display and modify the contents of a file.  

* create a file  
        `$ cat > filename`  
        Hello World    
        Ctrl+d (To save the file)   

* To display the content of the file   
`$ cat filename `
* To append the data in the already existing file  
`$ cat >> <filename>`  
Ctrl+d  (to save the changes) 
 
* Creating multiple files at same time using touch command  
`$ touch <filename> <filename> <filename>`  
`$ touch file1  file2  file3`  
 Note: to check the files use `ls` command. 

#### Creating a Directory: 
* Creating a directory  
Syntax: `$ mkdir  <dir name>`  
`$ mkdir mydir `

* Making multiple directories inside a directory  
`$ mkdir –p Technology/{frontend/{angularjs,reactjs},backend/{nodejs,jsva},cloud/{AWS,Azure,GCP}}`   

* Check it by using tree command or ls –R command   

#### Copying files  
* Copying files into directory   
Syntax: `cp <source filename> <destinatio directory>` \  
`cp file1 ktdir `  
 
 
* Copying directories from one location to other    
Synatx: `cp –rvfp  <dir name> <destination name>`   
`$ cp –rvfp ktdir2 ktdir `    
 
* Moving files from one location to other (cut and Paste)  
Syntax: `$ mv  <filename>  <Destination directory>`  
`$mv file2 ktdir `  
 
* Moving a Directory from one location to other   
Syntax: `#mv <dir name>  <destination dir name>`  
`$ mv ktdir ktdir2`  
 
#### Renaming a File and Directory 

* Renaming a File    
Syntax: `#mv <old name>  <new name>`  
`$ mv sample.txt kernelfile `  
 
* Renaming a Directory (The procedure and command for renaming the directory is exactly same as renaming a file.)  
Syntax: `$ mv old name  new name`    
`$ mv ktdir kerneldir `    
