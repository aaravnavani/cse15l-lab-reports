# Lab 1 Lab Report

## **Share an example of using the command with no arguments.**
* `cd`: `cd`
![Image](cd1.png)

When this command was run, the working directory is `/home/lecture1`. There was no output, but after the command was run, the working directory changes to `/home`
This is because there was no argument passed into `cd`, so it goes back to the root directory. The output is not an error. 
* `ls`: `ls`
![Image](ls1.png)

When this command was run, the working directory is `/home/lecture1/`. The output is all the files and folders that are stored in the lecture1 folder. The output is
not an error. 
* `cat`: `cat`
![Image](cat1.png)

When this command was run, the working directory is `/home/lecture1/`. Because we passed in no arguments to `cat`, it reads from the terminal since it doesn't have any file to read. Thus, when you type something the `cat` command just outputs whatever you type. The output is not an error. 


## **Share an example of using the command with a path to a directory as an argument.**
* `cd`: `cd messages`
![Image](cd2.png)


When this command was run, the working directory is `/home/lecture1/`. There is no output, but the working directory changes from `/home/lecture1` to `/home/lecture1/messages`.
The output is not an error. 
* `ls`: `ls messages`
![Image](ls2.png)


When this command was run, the working directory is `/home/lecture1/`. The output is all the files and folders in the `messages` folder. The output is not an error. 
* `cat`: `cat messages`
![Image](cat2.png)


When this command was run, the working directory is `/home/lecture1`. This results in an error because `cat` only takes an argument that is a file and it doesn't 
accept a directory. Thus, the output is an error: `cat: messages: Is a directory`. 

## **Share an example of using the command with a path to a file as an argument.**
* `cd`: `cd Hello.java`
![Image](cd3.png)

When this command was run, the working directory is `/home/lecture1/`. This command results in an error because the argument that is passed in, `Hello.java`, is not a 
directory and `cd` only accepts files as arguments. Thus, the output is an error: `bash: cd: Hello.java: Not a directory.`
* `ls`: `ls Hello.java`
![Image](ls3.png)

When this command was run, the working directory is `/home/lecture1/`. The output is just `Hello.java` because `ls` prints out all the files in the current working directory. Because a file is passed in as the argument of the `ls` command, it just prints the file name (`Hello.java` in this case). The output is not an error. 

* `cat`: `cat Hello.java`
![Image](cat3.png)
When this command was run, the working directory is `/home/lecture1/`. The output is the contents of `Hello.java` because `cat` prints out the content of a file that is passed in. The output is not an error. 








