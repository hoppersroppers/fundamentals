# Bash Internals and Unix Philosophy
## Unix Philosophy

The Unix philosophy is a loose idea on how Unix OSs should be written and operate. In order to understand the Bash shell, an appreciation of this philosophy is recommended. To be clear, this is not written down anywhere in an official capacity, but is more of an oral tradition.

From Doug McIlroy, an early Unix developer:
> "This is the Unix philosophy: Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface."

Under this philosophy, many of the design considerations that we see 40 years later make a lot more sense. When we are in the terminal, we are transported back to the old days where everything fit this philosophy. Modern programs don't care as much about these things because they are limited by things like size, processing power, or connectivity, but when you are in the terminal, you're in the Unix world.

Another core piece of the Unix philosophy is that "Everything is a file". By treating not just files and directories as streams of bytes exposed through the file system but also keyboards, printers, network connections, and process lists, Unix makes everything an I/O device. More on that later.


## POSIX

In the early days of Unix, it rapidly gained popularity due to its "manufacturer neutral" design that allowed it to be run on most hardware. However, competing Unix distributions had slightly different implementations which caused programs to not work across them. The way to fix this was to create a standardized method of interacting with the kernel and other processes. This standard is now known as the POSIX Standard. By following this standard, programmers in any language could be confident that their software would be able to run on any platform because they all used the same Programming Interface.

As a weird note, Bash itself is not fully POSIX-compliant, only POSIX-compatible. There is a ton of complexity there, but we will get away with ignoring it.

## What Does All of That Mean?

Alright that was a bit rambling, but here's the takeaway. Everything in the terminal should be able to speak to each other, because everything speaks the language of text streams in the same way. We saw that in the last section where we ran ```echo Hello World! > file1 ```.

Let's get into that a bit.

## STDIO

STDIO stands for Standard Input and Output. This standardized way of handling data streams, built upon the POSIX standard, allows all programs that use STDIO to be able to pass data between them in a controlled manner.

When an STDIO process begins, three data streams are opened:
* STDIN (file descriptor 0)
  * Standard Input - Often keyboard presses, but can also be the redirected from another file or command
  * File handle 0 means that you can specify STDIN with 0, STDOUT with 1, etc if you want to shorten a command
* STDOUT (file descriptor 1)
  * Standard Output - Sent to the terminal for display by default, but can be redirected into a file or another processes STDIN
* STDERR (file descriptor 2)
  * Standard Error - Usually sent to the terminal for display, this is a dedicated stream that programmers can use to send error messages
  * Independent of STDOUT, STDOUT can be hidden/redirected while STDERR can be displayed/redirected as required

# Practical STDIO

Enough reading, back to the terminal.
Let's go back over these commands now that we know what we are doing.

In a new directory with nothing in it, run these commands.
```
$ echo Hello World! > file1
$ echo Goodbye >> file1
```

Use ```cat``` to see what this looks like. Hopefully you aren't surprised what occurred.

We called these > "redirectors" in the previous chapter, but what they actually do is take the STDOUT of the echo command, and send it to a file. Single '>' tells Bash to fill in file1 starting from the beginning, while two '>>' tell Bash to append (just a fancy word to add to the back) to the end of the file. How does Bash know where the end of the file is? Glad you asked.

Basically, Bash walks through each character in file1 until there are no more characters to read, and then adds to that old stream and resaves it as a new stream.

We can also use ```1>``` to redirect STDOUT to a file because 1 is the file descriptor (FD), though it is not necessary.
If we want to redirect STDERR to a file, we can use ```2>```, as 2 is the FD for STDERR.
If we want to redirect STDOUT and STDERR to a file, we can use ```&>```. This "&" represents both FD 1 and 2.

There is a lot more to do with this, but this should be good for now.

# Pipe

Alright, here is where it all comes together. The magic happens when we redirect the STDOUT of one command to the STDIN of another command using a pipe. Pipes are a form of redirection, but instead of going to files, the redirected streams go to other commands.

Pipes are represented with ```|``` and are one of the more powerful tools we have as we can chain together commands. The Unix philosophy contains "Write programs that do one thing and do it well", so if we chain together programs using their STDIO text streams, we can do a lot of things well.

It is important to note that pipes are unidirectional and only pass data from left to right.

An example of what we can do with this is write a basic pipeline that can count the number of words in a file.

Run these commands first to create a file filled with words. By using append (```>>```) we do not overwrite the original file.

***Hint: Use the Up Arrow key on your keyboard to see the last command you typed. Then all you have to do is change a small amount of the command instead of retyping it***
```
$ echo cat dog sheep cow dog cat > animals
$ echo cat dog sheep cow dog cat >> animals
$ echo cats >> animals

```
***Hint: Type !! and press enter to rerun the last command you typed.***

```
$ !!
```

Use ```cat``` to verify what is in animals. You should see two lines of with the long list of animals, and two lines with just cats.

Now, let's use some pipes. First, I will introduce the command named ```uniq```. Use ```man uniq``` to learn what it does. Notably, it only checks for matching lines adjacently. Luckily, in animals right now, our matching lines are adjacent! So let's try out our first pipeline.

```
$ cat animals | uniq
```

The STDOUT of animals (four lines) is redirected to the STDIN of ```uniq``` which then checks for adjacent matches and removes them, leaving only two lines of output.

Let's make this more complicated. Add another line of text to animals using ```echo cat dog sheep cow dog cat >> animals```. Use the Up Arrow to navigate to that old command and run it again.

At this point you should have five lines, with lines 1,2, and 5 matching. Let's run ```cat animals | uniq``` again and we will see what comes out.

Unsurprisingly, we get three lines of output, with lines 1 and 3 matching. This is because uniq only sorts adjacent lines. To get around this, we can sort our lines ahead of time, using the command, ```sort```. Check the man page for sort if you want to learn more, then run the pipeline with ```sort``` in the middle.

```
$ cat animals | sort | uniq
```

Now we got getting what we are hoping for! Only two lines, and both are unique. We can pipeline as many commands as we want together, which gives us a ton of programming ability just from the command line. As you learn more commands (or get comfortable using ones you don't know from cheatsheets) you will become more and more capable.

# tee

Alright, final thing for STDIO, promise. ```tee``` is a command named after T-shaped piping in real world plumbing. What it does is pass the STDIN from another command's output through, while also writing a copy to a file.

Usage would look like this:

```
$ cat animals | tee unsorted | sort | uniq > sorted
```

Think about what just happened. For your assignment, write out what STDIN, STDOUT, and STDERR are and what they are doing for each of the commands. Answer in the usual format.

```markdown
Questions:

1. cat
2. tee
3. sort
4. uniq

Resources:

0. Google
```

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



# Text-Fu
head

tail

less

# Search
grep

regex

find

# Complicated Shit

Vars /global /local
eNV  
set vars locally
export vars
presets  
bashrc


# Bash Scripts
