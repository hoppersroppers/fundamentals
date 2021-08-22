# Command Line Basics
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
[<img src="https://imgs.xkcd.com/comics/command_line_fu.png">](https://xkcd.com/196/)

Pull up your terminal (ctrl-alt-t for the cool kids) and let's get after it!

First command we are going to type will tell us who we are, which is clearly badasses.

```
$ whoami
```

The next command will tell us our path within directory, also known as our working directory. On Linux, we call folders directories because it sounds cooler, don't get thrown off.

```
$ pwd
```
Lets print out the long names of everything in our current working directory with ```ls -l```. The -l is a flag that tells ls to print the "long" file information.

```
$ ls -l
```

This showed everything in our directory. Now let's go make a new directory inside this one to play in.

```
$ mkdir linuxPlayground
```

To enter this newly created directory, use the "change directory" command. Instead of typing out all of "linuxPlayground" use bash's autocomplete feature by pressing tab once you have a few characters typed, then press enter. This is super helpful, you can use autocomplete for basically anything.

```
$ cd linuxPlayground
```

Check where you are with ```pwd```.

List out the files in this new directory with ```ls -l```.
Unsurprisingly, it's empty.

To get back to the previous directory, type the command.

```
$ cd ..
```
The ".." is a strange concept but basically means "go up one level". If you wanted to go up two levels, you would type ```cd ../..```

Alright, ```cd``` back into the linuxPlayground directory.

Once you are in there, let's print something to the terminal.

```
$ echo Hello World!
```

This is nice, but now let's save it to a new file.

```
$ echo Hello World! > file1
```

That arrow is known as a redirector and can be used to redirect the output of commands to files.

Now use ```ls``` to check how many files there are, you should see file1.

Use the new command ```cat``` to read the contents of file1. Use the tab autocomplete so you don't have to type the whole thing.

```
$ cat file1
```

Sweeeeet. We're starting to go somewhere.

Now let's append (that means add to the back of) file1.

```
$ echo Goodbye! >> file1
```

As a note, we used two redirectors there. If we only use one it makes a new file, but two redirectors tells the bash shell to append to the back of an existing file.

Use ```cat``` to read file1. What do you see?

Lets now make a copy of file1.

```
$ cp file1 file2
```

Use ```ls``` to print out all files in your directory , then ```cat``` file2.
Now use ```mkdir``` to make a new folder named folder1. We'll save this for later.

Now let's learn how to delete file1.

```
$ rm file1
```

Use ```ls -l``` and voila! file1 is gone! (you should also see folder1 now)

While you have the results of ```ls -l``` up, look at what information is being shown for file2.

The output of ```ls -l``` should look like this:
```
drwxr-x--- 2 username groupname 4096 Jan 21 14:02 folder1
-rwxr-x--- 1 username groupname 15 Jan 21 14:02 file2
```
We won't beat this up too hard for now, but know that we can see:


* The first bit tells us what type of file it is
  * "d" means directory
  * "-" means normal file
  * There are more options that can go here, but it doesn't matter for Now
* The next 9 bits are permissions bits
  * You will learn more later, but they follow the read/write/execute format for the file owner/group/and others
  * You don't really know what that means, so don't worry for now
* The next bit, a number, tells us how many hard links there are to the file, but don't worry about it
* The first name is the username who owns the file, in this case you
* The second name is the group who owns the file. Unless you've setup a group already, this should also be your username
* The next number is the file size in bytes
  * Directories are always 4096, but individual files should be the number of bytes that make them up
* The next numbers should be the date and time last modified. These are not forensically accurate, but are good enough to sort by timestamp.
* Finally, the name of the file you are looking at the details of.

Okay that was a bit, don't worry too much about permissions and links and groups, but refer back to this when you have questions, or just Google "what does ls -l show"... you'll probably get a better description than mine!

Back to the command line!!!!!

Run the ```touch``` command to update the timestamp on file2.

```
$ touch file2
```

Use ```ls -l``` to verify the timestamp was updated.

Touch also has the ability to make a new empty file with the timestamp set for now.

```
$ touch file3
```

Use ```ls -l``` to verify the new file exists.

We will use the command ```mv``` to move file3 into folder1.

Use ```ls -l``` to verify the folder was created.

```
$ mv file3 folder1/

```

Use ```cd``` into folder1 and use ```ls``` to verify file3 is in there.


Alright, now let's delete folder1. Try to use ```rm folder1``` but it will tell you that folder1 is a directory. To delete it, use the "-r" flag, for recursive. ```rm -r folder1``` will delete everything in folder1 recursively, including other folders underneath. This is a dangerous command as you can accidentally delete things with it if you ```rm -r``` the wrong directory. ```rm``` is unforgiving, if you delete with it, the files are gone and will not be saved in Ubuntu's Trash. Sure the file might still be on your hard drive, but you're probably not good enough for recovering that yet. ```rm``` is often referred to as a "footgun" in the nerd community, as you probably will shoot yourself in the foot with it at some point.

Alright, that was a lot. We learned a ton of commands, and you're probably a bit stressed right now about what didn't make sense to you.

Use the command ```history``` to pull up your most recent commands and leave them on the screen.

Then work through it and take notes on what you still don't understand about what was described in this section. Once you have your questions, answer them like you normally answer Pre-Questions, one level of recursion deep. Submit your response in this format.

```
 Pre-Questions:
1.
2.
3.

Resources:

 Post-Questions:


 Feedback:

```

##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
