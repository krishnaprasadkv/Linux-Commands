# grep:-

* Grep: Grep stands for <b><i>Global Regular Expression Print</i></b>. It is used to pick out the required expression from the file and print the output. If grep is combined with another command it can be used to pick out the selected word, phrase from the output of first command and print it. 
 

### Examples of Grep:

* Consider the below file as an input.
```
# cat samplefile.txt
Welcome to linux command line interface
WElcome to Linux World
Krishna Prasad KV
learn operating system.
Linux command are easy to Learn.
```

* Let us pick the word *Krishna* from the file samplefile.txt 

$ `grep Krishna  samplefile.txt`
```
$ grep Krishna samplefile.txt
Krishna Prasad KV
```
 
* To avoid case sensitivity of the word (i.e. the word may be uppercase of lowercase) use -i   
$ `grep -i welcome samplefile`   
(lets grep the word welcome whether upper of lower case in the file samplefile.txt) 
```
# grep -i welcome samplefile.txt
Welcome to linux command line interface
WElcome to Linux World
root@DESKTOP-JDIP4H0:/home/krishnaprasadkv/krishna#
```
  
* To display a word and 1 lines after the word   
$ `grep -nA1 World samplefile`   
 
```
$ grep -nA3 World samplefile
2:WElcome to Linux World
3-Krishna Prasad KV
``` 

* To display a word and 1 lines after the word  
$ `grep -nB1 World samplefile`   

```
$ grep -nB1 World samplefile
1-Welcome to linux command line interface
2:WElcome to Linux World
``` 

* To display the things except the given word  
$ `grep –v kernel  ktfile`   
```
$ grep -v linux samplefile
WElcome to Linux World
Krishna Prasad KV
learn operating system.
Linux command are easy to Learn.
```
* To display the searched word in color  
$ `grep  --color  linux samplefile`  
```
$ grep --color linux samplefile  
Welcome to linux command line interface
```
 
#### Combining grep with other commands 
* Pick the word *Linux* from the file samplefile.txt   
$ `cat samplefile | grep World`   
(pipe | is used to combine to commands)   
```
$ cat samplefile | grep Linux
WElcome to Linux World
Linux command are easy to Learn.
```
* List the files and directories with the name of *sample*  
$ `ls -l | grep sample`
```
$ ls -l | grep sample
drwxrwxrwx 1 root krishnaprasadkv 4096 May 27 14:45 sampledir
-rwxrwxrwx 1 root krishnaprasadkv  139 May 30 14:30 samplefile
```
* List the localhost ip address    
$ `ifconfig | grep 127`
```
$ ifconfig | grep 127
          inet addr:127.0.0.1  Mask:255.0.0.0
```

* List help page of grep command with their option.   

$ `grep --help`
```
grep --help
Usage: grep [OPTION]... PATTERN [FILE]...
Search for PATTERN in each FILE or standard input.
PATTERN is, by default, a basic regular expression (BRE).
Example: grep -i 'hello world' menu.h main.c

Regexp selection and interpretation:
  -E, --extended-regexp     PATTERN is an extended regular expression (ERE)
  -F, --fixed-strings       PATTERN is a set of newline-separated strings
  -G, --basic-regexp        PATTERN is a basic regular expression (BRE)
  -P, --perl-regexp         PATTERN is a Perl regular expression
  -e, --regexp=PATTERN      use PATTERN for matching
  -f, --file=FILE           obtain PATTERN from FILE
  -i, --ignore-case         ignore case distinctions
  -w, --word-regexp         force PATTERN to match only whole words
  -x, --line-regexp         force PATTERN to match only whole lines
  -z, --null-data           a data line ends in 0 byte, not newline

Miscellaneous:
  -s, --no-messages         suppress error messages
  -v, --invert-match        select non-matching lines
  -V, --version             display version information and exit
      --help                display this help text and exit

Output control:
  -m, --max-count=NUM       stop after NUM matches
  -b, --byte-offset         print the byte offset with output lines
  -n, --line-number         print line number with output lines
      --line-buffered       flush output on every line
  -H, --with-filename       print the file name for each match
  -h, --no-filename         suppress the file name prefix on output
      --label=LABEL         use LABEL as the standard input file name prefix
  -o, --only-matching       show only the part of a line matching PATTERN
  -q, --quiet, --silent     suppress all normal output
      --binary-files=TYPE   assume that binary files are TYPE;
                            TYPE is 'binary', 'text', or 'without-match'
  -a, --text                equivalent to --binary-files=text
  -I                        equivalent to --binary-files=without-match
  -d, --directories=ACTION  how to handle directories;
                            ACTION is 'read', 'recurse', or 'skip'
  -D, --devices=ACTION      how to handle devices, FIFOs and sockets;
                            ACTION is 'read' or 'skip'
  -r, --recursive           like --directories=recurse
  -R, --dereference-recursive  likewise, but follow all symlinks
      --include=FILE_PATTERN  search only files that match FILE_PATTERN
      --exclude=FILE_PATTERN  skip files and directories matching FILE_PATTERN
      --exclude-from=FILE   skip files matching any file pattern from FILE
      --exclude-dir=PATTERN  directories that match PATTERN will be skipped.
  -L, --files-without-match  print only names of FILEs containing no match
  -l, --files-with-matches  print only names of FILEs containing matches
  -c, --count               print only a count of matching lines per FILE
  -T, --initial-tab         make tabs line up (if needed)
  -Z, --null                print 0 byte after FILE name

Context control:
  -B, --before-context=NUM  print NUM lines of leading context
  -A, --after-context=NUM   print NUM lines of trailing context
  -C, --context=NUM         print NUM lines of output context
  -NUM                      same as --context=NUM
      --color[=WHEN],
      --colour[=WHEN]       use markers to highlight the matching strings;
                            WHEN is 'always', 'never', or 'auto'
  -U, --binary              do not strip CR characters at EOL (MSDOS/Windows)
  -u, --unix-byte-offsets   report offsets as if CRs were not there
                            (MSDOS/Windows)

'egrep' means 'grep -E'.  'fgrep' means 'grep -F'.
Direct invocation as either 'egrep' or 'fgrep' is deprecated.
When FILE is -, read standard input.  With no FILE, read . if a command-line
-r is given, - otherwise.  If fewer than two FILEs are given, assume -h.
Exit status is 0 if any line is selected, 1 otherwise;
if any error occurs and -q is not given, the exit status is 2.
```
