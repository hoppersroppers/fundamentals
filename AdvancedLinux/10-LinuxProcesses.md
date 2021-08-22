# Linux Processes 
Suggested Soundtrack: [Don't Fear the Reaper](https://www.youtube.com/watch?v=FS8p_F0Stog). Put it on loop.

# Here be dragons! 

"Here be dragons" ('hic sunt dracones' in Latin) means dangerous or unexplored territories, mimicking a trend of old-timey map makers putting illustrations of dragons and sea monsters on uncharted areas of maps. It wasn't all that common, but at least it sounds cool.

Well, we've talked about most parts of the operating system, but now we are getting to where the magic happens, and also the dragons.

I'll still abstract away most of the complexity, don't worry, but this is where I am going to show you the existence of a bunch of complexity, explain the important stuff, and then we will all pretend the complexity doesn't exist so we can go the rest of our lives without having the cursed knowledge that our computers are filled with dragons, and those dragons are filled with dragons.  

What is a process? Any time you run a program, which includes any command you run in the shell, as well as the shell itself, as well as programs run by the OS, a process is created. Each of these processes runs in memory on the CPU, and that is all I am going to really tell you about the specifics of them in this course. Unless you decide to become an expert in a field directly next to Linux processes, the only things you need to know about processes are how to identify them, modify them, and kill them, so that is what we will do. 

## ps & top

The most common way to view processes is by running the ```ps``` command. To list all the  processes owned by a username, run this command:
```
$ ps -u <username>
```
This will return results in the format: 
```
PID TTY          TIME CMD
  954 tty2     00:00:28 Web Content
1262 pts/1    00:00:00 ps
 7020 ?        00:08:38 evince
... and many more
``` 

PID stands for process ID, and is the unique identifier associated with a specific process. They generally increment as new processes are started. TTY stands for TeleTYpewriter, which is a relic of early computing history. Today it tells us the file name of the terminal connected to standard input. Here we can see "tty2",. which tells us second terminal. We can also see "pts/1" for the TTY that ran the ```ps``` command. 'pts' stands for "pseudo terminal slave" and generally is a tab or SSH connection in a terminal.  

[<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/62/Termios-script-diagram.svg/711px-Termios-script-diagram.svg.png">](https://en.wikipedia.org/wiki/File:Termios-script-diagram.svg)


(***Note:*** The use of racially charged terminology such as "master/slave" and "whitelist/blacklist" have been identified as not appropriate in the modern era by the Linux Foundation and most reasonable people. The Linux project has officially stated that no further code or documentation will be accepted using this  outdated language and must be written using more inclusive terms, however, older code will remain unchanged. 'pts' as an acronym will likely never change, and eventually will be even more of an archaic piece of trivia than it already is.)

A 'pty' is a "pseudo terminal device" is an emulated terminal, and hosts multiple 'pts' inside it. Finally, if we see a '?' it just means the TTY is unknown. 

The more common way you will see the ```ps``` command is this:

```
$ ps aux
```

This returns all the data about all the processes running on the computer. You can check out in the man pages to see exactly what the 'aux' does. 

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1 173320 16324 ?        Ss   Mar22   2:28 /usr/lib/systemd/systemd 
student  32529  0.0  0.0 226464  5352 pts/7    Ss+  Mar30   0:00 bash
root     30555  0.0  0.0 257044 10092 pts/3    S+   10:16   0:00 sudo wireshark
avahi      975  0.0  0.0  32136  5440 ?        Ss   Mar22   1:08 avahi-daemon: running 
```
Now in addition to PID, TTY, TIME, and CMD, we have some new options. USER is interesting and shows who owns each process. Interestingly, some of these users aren't us, but are users specifically made to run a process. These processes are called daemons and can be defined as a computer program that runs as a background process, rather than being under the direct control of an interactive user. 

Looking at the results above, we can see the avahi-daemon process run by the avahi user. A second daemon (traditionally indicated by the trailing "d" in the name) we can see is systemd, which has the PID of 1. PID of 1 tells us that systemd is the init process, or initialization process that all processes on the computer were spawned from. Systemd does a ton of stuff, there's a lot of (dumb) controversy around it, just know it exists and that it is the init daemon (the process which starts all the other processes) for modern Linux and move on with your life. 

Other options visible are %CPU AND %MEM, which tell you exactly who is hogging your resources. VSZ is the Virtual Memory Size and tells us how much total memory is allocated to the process. RSS is the Resident Set Size and is used to show how much memory for that process is in RAM. There is an important distinction between the two about swap space and virtual memory that I don't want you to rabbit hole about (too hard), but I am going to ignore it in this course. 

Again we have TTY and then STAT, which tells us the current status of the process. There are a bunch of different STAT codes, if you need to understand them ```man ps``` and check out the section under the "PROCESS STATE CODES". 

START gives us the starting time of the process, or the date if it has run for over 24 hours. TIME gives us the total CPU time the process has been running. 

Finally, COMMAND gives us the extended version of CMD, with the path and all the arguments that a process was executed with. 

If we only want to look for a single type of process, we can grep for it using a pipe! 

```
$ ps aux | grep bash
```
If we only care about who is using the most resources, we can use a new command ```top``` to check them out!

```
$ top
```

This is especially useful if you are locking up and need to kill a  memory hog... speaking of, how do we do that? 

## Killing Processes

If you have the process ID, you can simply type ```kill``` followed by the PID. ```top```, or ```ps | grep``` are great for finding those PIDs. 

```
$ kill 1234
```

If you want to kill all processes with a certain name, ```pkill``` is very useful and gets the job done. Great for killing netcat listeners or python scripts when you are doing a bunch of things in a bunch of terminals. 

```
$ pkill nc
```

Once you've killed a process, run ```ps``` again to make sure you got it. If something went  wrong you might need a different kill option, or worse, made a zombie!

## Types of Processes

Alright, before we get to zombies, let's talk about parent and child processes. 

```
$ ps -ef
```
Running this we see a bunch of similar columns as before, but now we see a column labled PPID, or "Parent Process ID". This is the PID of the process that spawned the process listed, so we can use it to understand who is calling who (especially if we see processes and don't know where they came from).


An ever better way to visualize this is this command:

```
$  ps -e -o pid,args --forest
```
We can see a very interesting output that shows the parents, children, and grandchildren, and even further down. We can even see the command and the arguments we passed to display this. 

```
23453  \_ /usr/libexec/gnome-terminal-server
 5868  |   \_ bash
26785  |   |   \_ ps -e -o pid,args --forest
22769  |   \_ bash
22812  |   \_ bash
``` 

There is a lot of processes up towards the top of that printout that will have dozens of children. These are the key processes run by the operating system that makes everything work (like systemd). Don't worry about understanding them, but it's good to be able to find what things are every once in a while.

So Parent Processes are the processes which call another process, which is then called the Child Process. That Child Process can then start another process of their own, and they become the Parent Process of that Child Process. So in the example above, PID 23453 is the parent process of child process with the PID of  5868, which is the parent process of child process PID 26785. This makes PID 23453 the grandparent process of PID 26785. 

When a child process is started, the OS keeps track  of it and associates it with the parent. When the child process exits, completion is reported to the parent and the process is "reaped" from the process list. This "reaping" saves space in memory and is important for normal operation.

Orphan processes are processes whose parent process completed execution and exits (or was killed) prior to the child process completing. To handwave some complexity, the OS keeps track of parent and child relationships and informs the parent when the child has died.  If the parent has died, the child is not informed, and it just continues to run as normal. This means is that the process will run for however long it is supposed to, and during this time it will be referred to as an orphaned process. When the child completes, the OS sees that the parent process is dead and will "reap" the orphaned process itself with systemd, the init daemon with PID 1 we discussed earlier in the section. Again, don't worry about how/why systemd and the OS do what they do, just accept it as a fact of life.

Following the same lines, when a child process has completed or exited, the process table is updated to reflect the new status. However, if the parent process does not check the process table to receive notification in a timely fashion, the finished child cannot be reaped. As long as the parent process is alive, the OS will not step in and "reap" by itself. This is referred to as a "zombie" process, which will not be removed from the process table until the parent checks in on it and reaps it.  
 
Pretty spooky stuff to find in a conversation about processes, eh?

This stuff is all super complicated but honestly, don't worry about it too much. It's mostly trivia, but it is useful to know and I don't want to be accused of not teaching the basics properly. 

## Backgrounding

Another very useful tool we have is backgrounding processes. 

First, let's run ```nc -l 1338"  in a terminal window, and open a new window.

Next run this command in the new window ```nc -l 1337 &``` to setup a netcat listener that "backgrounds" itself and returns control of the terminal to us. 

The output should look like [1] 23867, with the trailing number being, you guessed it, a PID. We can now check out with ```ps aux``` to see what these two PIDs look like. 

```
student  27347 0.0  0.0   8172  2184 pts/3    S+   11:06   0:00 nc -l 1338
student  27389 0.0  0.0   8172  2188 pts/3    S    11:03   0:00 nc -l 1337
```

Besides PID and the command issued, a notable difference is that the 'STAT' column shows S and S+. I mentioned above if you need to understand STAT codes, use ```man ps``` and check out the section under the "PROCESS STATE CODES". 

```
 Here are the different values that the s, stat and state output specifiers
       (header "STAT" or "S") will display to describe the state of a process:

               D    uninterruptible sleep (usually IO)
               I    Idle kernel thread
               R    running or runnable (on run queue)
               S    interruptible sleep (waiting for an event to complete)
               T    stopped by job control signal
               t    stopped by debugger during the tracing
               W    paging (not valid since the 2.6.xx kernel)
               X    dead (should never be seen)
               Z    defunct ("zombie") process, terminated but not reaped by its
                    parent
For BSD formats and when the stat keyword is used, additional characters may be
       displayed:

               <    high-priority (not nice to other users)
               N    low-priority (nice to other users)
               L    has pages locked into memory (for real-time and custom IO)
               s    is a session leader
               l    is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
               +    is in the foreground process group
``` 
Cool, we've seen some of those words before (most of them we haven't), like Zombie processes. Now, looking at it we can see that both of the target PIDs are in an interruptible sleep, with one being in the foreground. 

Using the command ```jobs``` we can see what backgrounded processes are running. Interestingly, if we run ```jobs``` in a different tab than where we ran the backgrounded listener, nothing will pop up. This is because they are in a different parent process, so ```jobs``` won't find them (Remember, computers are not magic).  Once we navigate to the tab we ran the backgrounded process in we can use the ```fg``` command to bring them forward. With no args ```fg``` will take the first item, otherwise we can specify with ```fg `%<job #>```. 

Now the backgrounded process is in the foreground, and we can check ```jobs``` and ```ps``` to show the status has changed. 


## Signals 

Signals are a complicated part of something called "Interprocess communication". Interprocess communication is the mechanism the OS provides so that processes are able to work with each other. It is all very complicated, so we are not going to worry about them too much, other than to tell you that they exist and give you a few examples. If you are deeply interested in them, check out [this resource](https://www.tutorialspoint.com/inter_process_communication/index.htm), but I don't recommend anything IPC for beginners: 99.5% of technical jobs will never even to know that IPC exists, but now you do, so... hooray?

Signals are notifications to a process that an event has occurred. There are a large number of signals, and you can look them up if you ever need them. The most common one you will experience and use is killing processes with signals, which is how the 'kill' and 'pkill' commands work, along with closing browser tabs and terminal windows at the lowest level.

But for now, let's do a quick demo on the other common thing we can do with signals.

Run the command ```  nc -l 1337 ``` and then press Ctrl-z. 

Ctrl-Z sends a signal to the OS which modifies the process and automatically stops the process' execution. Notably, it does not background the process, and we need to do that manually with the ```bg``` command to get it to continue execution in the background. Now we can check the status of the process with ```jobs``` or bring it back with ```fg```. 

Once you have brought that process back to the foreground and are waiting on it again, press Ctrl-C. This sends another type of signal to the OS and causes the process that is running to recieve an "interrupt signal". This will kill the vast majority of processes and is a great way to kill pesky hanging processes. 

As an important note; there are also things called "interrupts" and "exceptions" that are similar to signals, but instead of being generated by the OS, they are actually generated by the underlying hardware, usually when a fault occurs. Even worse, there are software interrupts and software exceptions.... so it's complicated. Long story short, if you see signal, that almost always mean OS generated. If you see interrupts/exceptions, try to figure out if they are software or hardware generated. It is all very complicated and will not apply to any beginner material, however, it is important that you get the difference between them all in case you see a reference to them.

# proc 

Remember how I mentioned that "everything on Linux is a file"? Well, I have a confession to make. The command ```ps``` doesn't find all that information for you... instead, it is reading a series of text files that the Linux kernel provides. That is right, you can ```ls /proc``` and by looking at the different files in that directory, can find all sorts of information. Now to make it even more complicated, the directories in /proc don't exist until you ask for them so ... things get pretty damn sketchy from there, so we are going to mostly ignore it, but again, it is good for you to know.



# Assignment: 

```
Questions:

1. Navigate /proc and look through a PID associated with a netcat listener. Briefly, what can you find in there?
2. How can we tell a process is a zombie file in ps? (Hint: Process State Codes)
3. What is the difference between a signal and an interrupt? What is an interrupt signal?
4. What is systemd? (Do not try to understand it, only what it does) 
``` 

Answer in the usual format, and I expect you to have a bunch of Pre-Questions, and so many unanswered Post-Questions. Here there be dragons, so don't worry about it. 

"Seasons don't fear the reaper
Nor do the wind, the sun or the rain, we can be like they are
Come on baby, don't fear the reaper..."

```
 Answers:

 1.
 2.
 3.

 Resources:


 Pre-Questions:


 Post-Questions:


 Feedback:

```