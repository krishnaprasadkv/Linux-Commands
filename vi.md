# VI    (Visual display editor)
## Overview
* The default editor that comes with the UNIX operating system is called vi (visual editor). Using vi editor, we can edit an existing file or create a new file from scratch. we can also use this editor to just read a text file.vi editor is most popular editor in linux.Other editors in Linux are emacs, gedit.

    * VI    (Visual display editor)
    * VIM   (Visual display editor improved)  
Syntax: `$ vi <filename_NEW> or <filename_EXISTING>` 

* It has 3 modes:  
1. Command Mode   
2. Insert mode (edit mode)   
3. Extended command mode   
 
Note: When you open the vim editor, it will be in the command mode by default. 
 
#### Insert Mode: 
 
| options       | Description           |
|:-----: |:---         |
| i | To begin insert mode at the cursor position |
| I | To insert at the beginning of line      |
| a | To append to the next word’s letter      |
| A | To Append at the end of the line |
| o | To insert  a new line below the cursor position |
| O | To insert a new line above the cursor position |

#### Command Mode: 
* Moving within a file  
k - Move cursor up  
j - Move cursor down  
h - Move cursor left  
l - Move cursor right  
   

| options       | Description           |
|:-----: |:---         |
|gg |To go to the beginning of the page |
| G |To go to end of the page  |
| w |To move the cursor forward, word by word  |
| b |To move the cursor backward, word by word |
| nw |To move the cursor forward to n words (5W)  |
| nb |To move the cursor backward to n words (5B)  |
| u |To undo last change (word)  |
| U |To undo the previous changes (entire line)  |
| Ctrl+R | To redo the changes|
| yy | Io copy a line |
|nyy | To copy n lines (5yy or 4yy) |
|p |To paste line below the cursor position |
|P |To paste line above the cursor position|
|dw| To delete the word letter by letter (like Backspace) |
|x |To delete the world letter by letter (like DEL Key) |
|dd|To delete entire line |
|ndd| To delete n no. of lines from cursor position(5dd) |
|/ |To search a word in the file|

## Extended Mode: ( Colon Mode) 
* Extended Mode is used for save and quit or save without quit using “Esc” Key with “:” 

| options       | Description           |
|:-----: |:---         | 
|Esc+:w|To Save the changes |
|Esc+:q|To quit (Without saving)|
|Esc+:wq|To save and quit|
|Esc+:w!|To save forcefully|
|Esc+wq!| To save and quit forcefully|
|Esc+:x |To save and quit|
|Esc+:X| To give password to the file and remove password|
|Esc+:20(n)| To go to line no 20 or n |
|Esc+: se nu| To set the line numbers to the file|
|Esc+:se nonu |To Remove the set line numbers|

* To open multiple files in vim editor  #vim –o file1 file2 To switch between files use Ctrl +w 
