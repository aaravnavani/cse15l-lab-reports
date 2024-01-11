# Lab 1 Lab Report

**Share an example of using the command with no arguments.**
* `cd`: `cd`

When this command was run, the working directory is `/home/lecture1`. There was no output, but after the command was run, the working directory changes to `/home`
This is because there was no argument passed into `cd`, so it goes back to the root directory. The output is not an error. 
* `ls`: `ls`

When this command was run, the working directory is `/home/lecture1/`. The output is all the files and folders that are stored in the lecture1 folder. The output is
not an error. 
* `cat`: `cat`

When this command was run, the working directory is `/home/lecture1/`. 


**Share an example of using the command with a path to a directory as an argument.**
* `cd`: `cd messages`

When this command was run, the working directory is `/home/lecture1/`. There is no output, but the working directory changes from `/home/lecture1` to `/home/lecture1/messages`.
The output is not an error. 
* `ls`: `ls messages`

When this command was run, the working directory is `/home/lecture1/`. The output is all the files and folders in the `messages` folder. The output is not an error. 
* `cat`: `cat messages`

When this command was run, the working directory is `/home/lecture1`. This results in an error because `cat` only takes an argument that is a file and it doesn't 
accept a directory. Thus, the output is an error: `cat: messages: Is a directory`. 

**Share an example of using the command with a path to a file as an argument.**
* `cd`: `cd Hello.java`

When this command was run, the working directory is `/home/lecture1/`. This command results in an error because the argument that is passed in, `Hello.java`, is not a 
directory and `cd` only accepts files as arguments. Thus, the output is an error: `bash: cd: Hello.java: Not a directory.`
* `ls`: `ls Hello.java`

When this command was run, the working directory is `/home/lecture1/`. 
* `cat`: `cat Hello.java`





