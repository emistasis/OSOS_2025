# Presentation follow along

## The Shell
### What is the shell?
The shell is a program that allows us to communicate with our computers by entering in commands. When the computer receives this command, it outputs a response. The shell is sometimes called the "terminal" or "command line." The most popular shell is Bash (which stands for Bourne Again SHell).

### What is the difference between the shell and the terminal?
**Shell:** interpreter that _processes_ your commands.

**Terminal:** visual interface ("window") where you _interact_ with the shell.

### Why would I use command line?
Humans interact with computers in many ways - most commonly through touch or speech recognition. Typically, when we interact with our computers, we use a graphical user inferface (GUI). For example, your file explorer on your computer (the application that you use to navigate all of the files stored on your device) is considered a GUI.

Any files that are generated in command line can be found using the file explorer and vice versa.

GUIs allow us to tell our computer what to do by clicking our mouse. GUIs are easy to navigate and use, but this isn't the best way to instruct the computer on what to do.

Imagine that we have a complex task, such as searching for all files in your computer that contain the words, "Open Source for Open Science," and storing all of names of those files into a new text file. Doing this with just a mouse and keyboard sounds like a nightmare. That's where command line comes in. We can easily search through all of the files on our computer to perform this task.

When we interact with our computers through command line, we refer to this as using the "command line interface" (CLI). Unlike GUI, CLI options are not presented to you. You can utilize the awesomeness of the command line _only_ if you know the commands to do so. This is why Bash is considered a programming language. Fortunately, unlike trying to communicate in a spoken foreign language, you can go a long way with programming languages by only knowing a few "words" or "commands."

### What happens when we open the command line?
When you first open the command line, you will be presented with a prompt. The shell most commonly uses a `$` as the prompt. 

You **do not** type the prompt. The command follows the prompt. 

Once you enter the command, you must press the <kbd>Enter</kbd>.

### What are the parts of a shell command?
There is the command, the options (also referred to as flags), and the arguments. Together, options and arguments can be referred to as parameters. Each part of the command should be separated by a space. Capitalization is usually important when writing commands.

<img width="350" height="187" alt="image" src="https://github.com/user-attachments/assets/55a73019-06f8-4acd-a14a-3c0534c0b01c" />

Options change the behavior of the command, while arguments tell the command what to operate on (e.g., the files and/or directory). A command can be called with more than one option and more than one argument, but a command doesn't always require either.

## Directories and paths
### How are directories structured?
<img width="792" height="1165" alt="image" src="https://github.com/user-attachments/assets/57f12df2-5981-40b4-9c4a-b580879e7b94" />

The working directory is the specific location where the program or command is operating.

### Relative vs absolute paths
The absolute path is the complete location (or path) to a file or directory (e.g., `/home/emmarie/documents`).

A relative path specifies a location based on the current working directory, using shortcuts like `.` for the current directory and `..` to move up a level.
 
The shell interprets a tilde (~) character at the start of a path to mean “the current user’s home directory”. 
For example, if my home directory is `/Users/emmarie`, then `~/data` is equivalent to `/Users/emmarie/data`. 

This only works if it is the first character in the path; `here/there/~/elsewhere` is not `here/there/Users/emmarie/elsewhere`.

## How can I create, copy, and delete files and directories?
### Creating directories

To create a directory, we first want to see where we are.
`pwd`

Create a new directory
`mkdir osos2025`

Move into the new directory
`cd osos2025`

Create a new file
`touch bash.txt` or `nano bash.txt`

Print all of the files in the directory
`ls -F`

### What are some best practices when generating files and directories?
* Don't use spaces in their names. Although spaces can make the name more human readable or meaningful, spaces are used to separate arguments and it confuses the computer.
* Don't begin with a `-` (dash).
* Stick with lowercase letters, numbers, `.` (periods), `-` (dash), and `_` (underscore).
  
### How can I edit files?
`nano bash.txt`
There are a couple of different ways to edit files. Some options are  Emacs, Vim, or Nano, which all take some time to learn.
In my personal experience, Notepad++ is the best option for Windows, BBEdit is the best option for Mac. If you're really into coding, then I suggest you using VSCode.

### What if I want to copy a file or directory?
`cp` allows you to copy either a file or directory. To copy it into a new directory, you do the following:
`cp bash.txt /bash/bash.txt`

### What if I want to remove a file or directory?
`rm`... but if you delete a file, it is **GONE FOREVER!!!** 

I recommend using `rm -i`, which prompts whether or not you really want to delete the file that you suggest.

### Is there a way to get help or better understand certain commands?
If you're using Git Bash (Windows) or Linux, you can add the flag `ls -h` or `ls --help` after.

If you're using a macOS, you'd want to use `man ls`. `man` in programming typically stands for "manual." You should see a massive list of all the potential commands you can use associate with the list `(ls)` command. If you are on a mac and have run this, you can type `q` to exit ("quit").

This is also a great example of short and long options for commands. Short options, which are typically just a letter `-h`, are helpful when typing commands directly into the shell to minimize the keystrokes and get things done faster. Long options are better for clarity `--help`.

### Stdout & Stderr
Standard output (or stdout) is the default location where the shell sends it normal output. Stdout is typically directed to the console / terminal where the command (or program, if you're running a specific program) is executed. 

You can redirected the stdout information into a new file. This can be helpful for information management. If you were to redirect this into a new file, you would run:
`command > newfile.txt`

If you were to redirect this into an already existing file that you don't want to override, you would run:
`command >> newfile.txt`

Standard error (or stderr) is special and prints out error messages, warnings, debugging and diagnostic information. The purpose of stderr is to provide information to you about what you need to correct without messing up the intended output. Sometimes, programs will run, but they want to alert you to something.

You can redirect the stderr information into a file as well. The most standard way to do this would be as follows:
`command 2> log.txt`

If you want to store your stdout in one file, and your stderr in another, you can run:
`command > out 2>error`

You could also redirect your stdout to a file (`>out`), and then redirect your stderr to that stdout file (`2>&1`).
`command >out 2>&1`

## Pipes & filters
Let's start by unzipping the folder that you downloaded off of the Google Drive. We are going to unzip and place the cats folder into the new OSOS2025 directory that we made previously.
`unzip cats.zip -d ~/osos2025`

### Print the number of lines, words, and characters (in that order)
`wc big_cats.txt`

### How can we store this information into a new file? What about looking at the contents of the file?
`wc *.txt > lengths_cats.txt
cat lengths_cats.txt`

### How to sort the file?
`sort -n`

### How can we see the first few lines? How can we see the last few lines?
`head -n 3 small_cats.txt > cats.txt
tail -n 2 big_cats.txt >> cats.txt # appends to the already existing file`

### What about combining multiple commands?
`wc -l *.txt | sort -n`

### How does piping work?
<img width="800" height="560" alt="image" src="https://github.com/user-attachments/assets/05d5a47b-a7a7-40c8-90a7-c0ea2266ac83" />

## Loops
Suppose that we have several hundred files for three species: Lion, tiger, and domestic cat. Each of the species' files have their taxonomic classification listed inside of them. Say that we want to extract the classification of all three species from all of the files. 

We can run a `for` loop on these files to extract the classifications.

```
for i in *spp.txt; do
  head -n 2 "$i"
  echo ", Extracted from $(basename "$i" _spp.txt)"
  echo;
done
```



