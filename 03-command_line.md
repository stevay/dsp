# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > 
* creating a directory = mkdir 'directoryname'
* deleting a directory = rm -r 'directoryname'
* creating a file using 'touch' command = touch 'filename.extension'
* deleting a file = rm 'filename'
* renaming a file = mv 'original_filename' 'new_filename' (in same directory)
* listing hidden files = ls -a
* copying a file from one directory to another = cp 'filename' 'directoryname'
* moving a file = mv 'filename' 'directoryname'
* listing hidden files in long format, with date and time = ls -alt

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`
`ls -a`
`ls -l`
`ls -lh`  
`ls -lah`  
`ls -t`
`ls -Glp`  

> > 
* ls = lists contents in a directory (does not include hidden files)
* ls -a = lists contents in a directory, including hidden files
* ls -l = lists all content in long format
* ls -lh = lists content in long format, and displays file sizes in more user-friendly units (e.g. B = Bytes)
* ls -lah = lists all content in long format, while displaying file sizes in more user-friendly units (e.g. B = Bytes)
* ls -t = lists files and directories by the time they were last modified
* ls -Glp = do not print group names; list all content in long format; indicator style = slash


---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > 
* ls -m = displays names as a comma-separated list
* ls -R = displays sub-directories as well
* ls -x = displays files as rows across the screen
* ls -d = displays only directories
* ls -F = flags file names

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > xargs reads data from standard input (stdin) and executes the command (supplied to it as an argument) one or more times based on the input read. Any blanks or spaces in the input are treated as delimiters, while blank lines are ignored. 'echo' is the defualt command xargs executes.
* you can explicitly specify any other command to xargs
* Example: 
* xargs -L 1 find -name 
* "*.txt"
* ".tmp"
* in the above example, find and -name are the commands / arguments sent to xargs; and "*.txt" + "*.tmp" are the file names we want to search as input through stdin

 

