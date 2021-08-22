# Advanced Bash Shell 
On the surface, the bash shell and all the things you can do with it seem very complicated. In what should be unsurprising at this point in the course, it's even more complicated when you try to understand why and how it works. Of course, you don't need to know most of it, just a few key portions that I'll go over right now.

This stuff is pretty hard and honestly, not that important, bordering on trivia. Still, I feel like I should teach it. 

# How Does Running a Command In Bash Work


When we type a command in the terminal and it is run, there is quite a bit going on under the surface. To understand how it really works, we have to look at our "environmental variables", which provide the information to the shell that is required for it to operate properly. These variables control the shell's behavior, guide access to resources, basically make it work... remember, there's nothing magic with computers, and this is "why" shells work.

## Your Environment
Okay, so variables. Where do we actually find them?

Using the command ```printenv``` we can print out all of our set environmental variables. Most of these aren't all that exciting or important, but a few are worth noting. 

#### SHELL
It was mentioned before in the class, but yeah, there are a ton of different types of shells. Different boxes will have different default shells, but generally, they are all close enough to bash to fake.  

A command I use all the time is ```printenv SHELL``` which will give you just the shell value, letting you know what you are working with. ```printenv``` can be used like that for all variables, but SHELL is definitely the most common.

#### TERM 
Describes the type of terminal to use when running the shell... you were just getting used to their being multiple shells, now there are multiple terminals?!?! Don't worry about it much, it's rarely relevant.

#### USER 
Saves the current logged in user. Try the command ```su``` to see what happens~

#### PWD
Saves the current PWD. When you run a command like ```ls``` or ```cat```, this is what tells the shell where you are. 

#### OLDPWD 
Saves the last PWD so that you can return to it using the ```cd -``` command. Super useful if you cd deep into something and want to cd back out no without "../../../../"-ing. Try it out!

#### _
Saves your last command so that you can access it for a variety of reasons, one of my favorites being the classic ```!``` command which reruns your previous command. It is particularly useful if you try to run a command, it tells you that sudo permissions were required, and then you can run ```sudo !``` to rerun the same command with the correct permissions. 

#### PATH

Path is going to look like a comma separated list of directories, usually in the /bin area. This is the list of places the shell will look for a binary when a user types in a command. For example, when a user types in "cat", the system will search these directories in order until it finds a binary named ```cat```. More on that next.

## More PATH

So as stated before, when you run a command it will search through the list of directories for the first binary that matches the name and execute it in your current "context". 

```
$ export PATH=$PATH:/home/dennis/bin
```
This command will set the PATH variable equal to the old PATH with ":/home/dennis/bin" appended to the end. Now when I run a command, if a program is not found in the first directories, it will search my user's /bin and attempt to run whatever is found there.

While this can be useful, it also can be the cause of a security problem. Imagine if instead of the command above we ran ```$ export PATH=/home/dennis/bin:$PATH```.

Now if we ran ```cat``` the first place checked would be the user /bin we just set, which we could fill up with whatever binary we wanted, named what we wanted. In some interesting attack scenarios, by changing PATH an attack can trick a user (or an automated script) into running a malicious version of a common binary. As always, security is complicated and gets more complicated the deeper we go.

To verify which executable is being found on your PATH, run the command ```which``` with the first argument the name of the command you want to run. It will print out the path of the executable that will be run. 

***As a note, if you are executing a local executable using the formal ```./executableName```, you will not use the PATH variable at all. The "./" specifies "in working directory" so there is no need to go searching.***

##  Set Variables 

```set``` prints all shell variables. ```printenv``` prints all environmental variables. The difference is a question of scope. Shell variables are only applicable for the local shell, while environmental variables are passed down to child processes. Does this matter to you really? No! But I will tell you about it hear anyway. Do this tutorial and remember that these are things, I will come back to it eventually. 

```
$ FOO="dennisIsGreat"
$ echo $FOO
dennisIsGreat
$ set | grep FOO
$ printenv | grep FOO
```

We looked at the ```export``` command above with PATH and didn't really explain it, so we will do it now. ```export``` adds a variable to the environmental variable group, which means it will now be available to any child processes, as well as the local shell.

```
$ export FOO
$ printenv | grep FOO
$ bash
   % echo FOO
   dennisIsGreat
$ unset FOO
$ set | grep FOO
$ printenv | grep FOO
$ export - n FOO
$ printenv | grep FOO
```
I bet you can guess what ```unset``` and ```export -n``` did and if not, ```man``` should help out. Hope this little adventure into variables didn't make your brain hurt too much, because mine sure hurts from writing it.

## Set Temporary Aliases

Much like setting variables, we are going to set an alias for a frequently typed command. Aliases are the Linux term for when we modify the ENV so that running a user-defined command runs a custom command. 

```
$ alias lsa=?ls -a?
$ lsa 
```



## Set Permanent Aliases

All of the things we just did were temporary and will disappear the next time you close out your terminal. Let's make all these changes permanent. Your shell is constantly updating its environmental variables so that it knows what the correct configuration is for any point in time, however, there is an initialized configuration the shell will load every time. This is known as your .bashrc file, and is located at ```~``` in your home directory.

Your .bashrc is part of a group of files called dotfiles, so named because they have a dot in front of their names which makes them "hidden" files in the Linux directory system. Dotfiles are almost always used to store configuration settings in Linux, and many people use them to customize their experience, such as using .vimrc files to tune Vim.  We will talk about them more later, don't run off on me yet. 

 ```cat ~/.bashrc``` to check out what is in yours, likely a lot of comments and things that are set equal to values . These variable assignments are critical to how shells function and define desired behavior. Don't worry about what they all do specifically, it doesn't matter much unless you care about modifying your .bashrc (as we will do later). 

Open up your .bashrc and add the appropriate lines to the end of it in order to permanently alias one command and set a permanent variable. If you are looking for motivation to make a more complicated one If you are interested in dotfiles, check out [this link](https://medium.com/@tzhenghao/a-guide-to-building-a-great-bashrc-23c52e466b1c) for more info. 

A .bashrc can be as complicated or simple as you like, and there is near endless customization possible. You will be able to carry this around between computers with you to automatically personalize the box as soon as you load in the .bashrc so its just like home. I recommend commenting it heavily  so you remember what things are, and then uploading it to Github so it's easy for you to bring to whatever computer you are using. Consider it a living document. Personally, I don't use them because I bounce around computers so often and I don't like building non-transferrable muscle memory, but they certainly have their benefits and most people love them.

# Bringing It All Back Together

So what happens when you run a command like 'nc -lp 1337' in your shell? 

Well, the first thing that happens is that the shell is reading STDIN to a buffer. When you press enter, the shell goes and breaks down what you typed into the command it needs to run.

Then the shell starts looking for an 'nc' binary in your environmental PATH. The first 'nc' that the shell finds is the one it will take, so as we discussed earlier, you only want to have one executable with with the specified name in your path or weird things are going to occur. You can determine which 'nc' will be used (ie is first in the path) with the ```which``` command.

Then the shell (which is a process with a PID itself) will fork, meaning it will spawn a new child process, and then that child process will "exec" the specified command, in this case, /bin/nc with the appropriate arguments. As a notable point, fork creates a new process, while exec replaces a process. The shell needs to fork first so that the exec occurs in the child process and replaces the child process, rather than replacing the shell itself, which would kill your terminal. This fork/exec process is how all child processes are created. Don't worry too much about exactly how this works for now, but if you are interested check out the man pages for 'fork' and 'exec. 

The parent process will continue running, independent of the child process, and with 'nc' waiting for an incoming connection we can look at our running processes with ```ps``` to identify our child and parent processes. 

Any output from 'nc' will be sent to STDOUT and STDERR, which will be displayed in the terminal. However, the terminal has the ability to background the child process, as described earlier, so if STDOUT and STDERR aren't being piped anywhere, noone will ever see them. 

These two processes are running independently now, and killing the parent does not automatically kill the child. However, you may have noticed that if you kill the terminal while  a process is running in it, you will be prompted if you want to kill the terminal and it's child process. This is slightly confusing, but it's because the terminal was programmed to send kill signals to its children when it closes  for the UX benefit, not because of any inherent property of parent and child processes. 

Alright, that was a bit much, but I'm glad we talked about it. 

For your assignment, discuss the process of what happens when you run 'ls', especially how the shell knows what location to print the contents of. Use the usual format. 

```
 Answers:

 1.

 Resources:
 

 Pre-Questions:


 Post-Questions:


 Feedback:

```