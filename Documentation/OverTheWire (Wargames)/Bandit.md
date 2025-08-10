# Intro
Welcome to my documentation of the OverTheWire War Games: Bandit edition! This documentation of my journey through each level, from the beginning to the final challenge. I aim to provide a straightforward, step-by-step process, illustrating the commands and logic I used to solve each puzzle. This isn't just a list of answers; it's a look into my process. I hope this documentation serves as a helpful and engaging resource. 


Im trying to make a table of content for my github text md file help me expand this table of content from level 1 through level 34:

## Table of Contents
* [Level 0](#level-0)
* [Level 1](#level-1)
* [Level 2](#level-2)
* [Level 3](#level-3)
* [Level 4](#level-4)
* [Level 5](#level-5)
* [Level 6](#level-6)
* [Level 7](#level-7)
* [Level 8](#level-8)
* [Level 9](#level-9)
* [Level 10](#level-10)
* [Level 11](#level-11)
* [Level 12](#level-12)
* [Level 13](#level-13)
* [Level 14](#level-14)
* [Level 15](#level-15)
* [Level 16](#level-16)
* [Level 17](#level-17)
* [Level 18](#level-18)
* [Level 19](#level-19)
* [Level 20](#level-20)
* [Level 21](#level-21)
* [Level 22](#level-22)
* [Level 23](#level-23)
* [Level 24](#level-24)
* [Level 25](#level-25)
* [Level 26](#level-26)
* [Level 27](#level-27)
* [Level 28](#level-28)
* [Level 29](#level-29)
* [Level 30](#level-30)
* [Level 31](#level-31)
* [Level 32](#level-32)
* [Level 33](#level-33)
* [Level 34](#level-34)

---

## Level 0
In Bandits level zero my first task is to log in using SSH. It gives me the username Bandit0 and the password Bandit0. The host that we are going to connect to is bandit.labs.overthewire.org.
Host: bandit.labs.overthewire.org
Port: 2220
Username/Password: bandit0
Command: ssh bandit0@bandit.labs.overthewire.org -p 2220

<img width="715" height="650" alt="image" src="https://github.com/user-attachments/assets/1164f5d4-91b9-4442-9d68-01e703567706" />

After you've successfully logged in as bandit0, run the ls command to list the files in the directory. You'll find a file named readme. To view the contents of this file, use the cat command. This will reveal the password for bandit1.

<details> <summary>Answer</summary> ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If </details>   

## Level 1
To begin, you'll need to SSH into Bandit 1. You can reuse the same command from the previous level, but simply replace bandit0 with bandit1. The command will look like this:

ssh bandit1@bandit.labs.overthewire.org -p 2220
You'll be prompted for a password. Use the password you found in the readme file from the previous level.

After successfully logging in, you'll see the goal for Level 1: "The password for the next level is stored in a file called - located in the home directory."

Normally, you would use cat to view the contents of a file, but because this file is named with a hyphen, using the cat - command will not work as expected. The terminal will interpret the hyphen as an instruction to read from standard input, not from a file.

To solve this, you need to tell cat that the hyphen is a filename and not a command option. You can do this by using the less than operator <.

Run the following command to retrieve the password:

cat < -
This will print the password for the next level directly to your terminal.
<details> <summary>Answer</summary> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx </details> 

## Level 2
The password for the next level is stored in a file named spaces in this filename.  The issue with this filename is that the cat command, by default, interprets each word separated by a space as a new, separate file. This means that running cat spaces in this filename would try to open four different files: spaces, in, this, and filename, which would all result in an error.

To solve this, you need to tell the shell that the entire string spaces in this filename is a single file. You can do this by enclosing the filename in double quotes.  While you could also use the less than operator (<) like in the previous level, using double quotes is a more direct way to handle filenames with spaces.

The correct command to retrieve the password is:

cat "spaces in this filename"
Executing this command will display the password for Bandit 3.
<details> <summary>Answer</summary> MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx </details> 

## Level 3
The goal for this level is to find the password, which is stored in a hidden file within the inhere directory.

First, run the ls command to list the files in your current directory. You will see a directory named inhere.

ls
Next, change into that directory using the cd command.

cd inhere
Now, if you run ls again, it will appear as if the directory is empty.  This is because the file containing the password is a hidden file. In Linux, any file or directory that begins with a dot (.) is hidden by default.

To reveal hidden files, you need to use the ls command with the -a flag, which stands for "all".

ls -a
This will show you a list of all files, including the hidden ones. You'll see a file named .hidden.

Finally, use the cat command to view the contents of the hidden file and get the password for Bandit 4.
<details> <summary>Answer</summary> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ </details> 

## Level 4
The objective for this level is to find the password for Bandit 5, which is stored in the only human-readable file within the inhere directory.

After connecting to Bandit 4, change into the inhere directory.

Use the ls -la command to list all files, including hidden ones, and you'll notice many files named something like  -file00,  -file01, etc. Most of these files are not human-readable.
<img width="899" height="486" alt="image" src="https://github.com/user-attachments/assets/22662832-aa88-4f4f-8aac-e823c45103c3" />

Instead of manually checking each file, you can use the file command to identify which file contains readable text.

This command will go through every file in the directory and tell you what kind of data each one holds. You will notice that most files are "data," but one will be identified as "ASCII text."
<img width="786" height="286" alt="image" src="https://github.com/user-attachments/assets/f18d15b3-1daf-47a1-9281-6c931933f747" />


Once you've identified the ASCII text file, use the cat command to view its contents and retrieve the password for Bandit 5.
<details> <summary>Answer</summary> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw </details> 

## Level 5
The password for Bandit 6 is in a specific file located somewhere within the inhere directory. The file has three properties: it's human-readable, exactly 1033 bytes in size, and non-executable.

First, change into the inhere directory.

cd inhere

Inside this directory, you'll find many subdirectories, making it impractical to search manually. Instead, you need to use a single command to find the file that matches all the given criteria. The find command is perfect for this.

<img width="902" height="841" alt="image" src="https://github.com/user-attachments/assets/c3530b41-2fe8-4bd7-8466-449946a20342" />

<img width="975" height="1041" alt="image" src="https://github.com/user-attachments/assets/41026dd9-0b6b-4831-b14c-06870421c168" />

Here is the command you'll use:

find . -type f -size 1033c ! -executable

This command searches the current directory and all subdirectories for a regular file (-type f) that is exactly 1033 bytes in size (-size 1033c) and is not executable (! -executable).

After running this command, you will get the path to the specific file. Now, use the cat command with the full path to view the file's contents and retrieve the password.

cat ./maybehere07/.file2

<img width="975" height="45" alt="image" src="https://github.com/user-attachments/assets/bab08009-2595-4de2-a9bc-0e621539eb5b" />


<details> <summary>Answer</summary> HWasnPhtq9AVKe0dmk45nxy20cvUa6EG </details> 

## Level 6
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 7
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 8
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 9
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 10
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 11
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 12
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 13
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 14
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 15
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 16
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 17
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 18
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 19
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 20
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 21
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 22
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 23
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 24
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 25
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 26
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 27
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 28
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 29
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 30
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 31
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 32
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level 33
... some content ...
<details> <summary>Answer</summary>  </details> 
## Level-34
... some content ...
<details> <summary>Answer</summary>  </details> 

