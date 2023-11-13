# The Shell

What is a shell? Basically, it is the command line interface that power
users (from this point forward, that includes you) control their
computer's operating system with. Windows has a shell, Macs have a
shell, and the Linux operating system has a shell. 

Linux is the name of the operating system that you will be learning
about for the rest of the course. For now, the only thing I want you to
know is that one of the primary shells for it, named Bash, was written
by Brian Fox, who is just a generally badass guy. [His Wikipedia page is
worth a
read](https://en.wikipedia.org/wiki/Brian_Fox_(computer_programmer)). 

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/abe/437/3e1/1643681800739.jpg"
class="fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/abe/437/3e1/1643681800739.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/abe/437/3e1/1643681800739.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/abe/437/3e1/1643681800739.jpg?width=1920&amp;dpr=3 3x"
style="width: 300px;" />

  

So to go back over what we just said, the shell runs in the operating
system which runs on the computer. In this course we will be teaching
you a ton about the terminal on the Linux operating system, and then a
little bit about the underlying computer hardware.

# Command Layout

So let's get into how the real hacker uses the command line, starting
with a scene from The Matrix, an all-time great hacker movie.

<iframe allowfullscreen height="360" src="https://www.youtube.com/embed/0PxTAn4g20U?wmode=opaque" width="640"></iframe>  

  

That scene is actually pretty realistic, and a lot of the commands she
runs are real things you will use throughout this course. 

Let's get into the format of commands. First, there is either going to
be a $ or a \#. Going forward, I will use a $ to indicate the beginning
of a command.

``` default
$ 
```

This indicates that you are in a shell of some format where you will be
able to type a command.

`$ command`

When you run a command from the terminal, the shell is what will execute
a program. These commands can do anything, from running a built-in
program to the operating system, executing a script you wrote, the limit
is what the command was programmed to do. We'll do a little programming
in this course too!

`$ command <argument>`

We can also modify the program's behavior by adding what are called
arguments. These arguments do things like configure settings, or tell
programs to operate in a certain way to do something, and specify where
to put output. To indicate an argument, we sometimes use something
called a "flag" which says to the shell, hey, I am trying to modify the
program that is running with the argument directly behind me. It looks
something like this:

`$ command -f <argument>`

This command tells the shell to run the program "command" with the flag
"-f" and the argument "argument". There can be dozens of flags and
arguments to modify a command or how a program runs, so it gets
complicated real quick. Luckily, there is a command named "man" we can
use to find out what exactly those flags and arguments do to modify the
command. We'll be best friends with "man" eventually, but for now, let's
run our first commands! 

Usually we would run a shell on a computer (like the Windows 'cmd
line'), or maybe in something known as a virtual machine which you will
set up later in this course, but we have an even cooler option these
days due to what can basically be described as dark magic: Shell In the
Browser! The Shell in the Browser I will have you use for this section
is a small Linux operating system with most of the same functionality as
a fully featured shell. 

  

<iframe height="500px" id="iframe" src="https://darin755.github.io/browser-linux?embed=true" width="750px">
</iframe>
<script>
// @license magnet:?xt=urn:btih:cf05388f2679ee054f2beb29a391d25f4e673ac3&dn=gpl-2.0.txt GPL-2.0
//load embeded
function start_vm()
{
document.getElementById("iframe").setAttribute("src", "https://darin755.github.io/browser-linux?embed=true");
}
//basic set message function
function sendMsg(msg)
{
document.getElementById("iframe").contentWindow.postMessage(msg);
}
// @license-end
window.onload = start_vm();

</script>

1\. There is a shell embedded in this page right above this which should
have finished loading by now. The same shell also lives here:
<https://www.hoppersroppers.org/shell/src/> 

Sometimes it takes a bit to load (\~10 seconds), if it takes longer than
30 seconds, just press refresh. How it works and understanding what we
are doing doesn't matter right now but by the end of the course, I
guarantee you'll get it.

2\. Once your in-browser Linux operating system has loaded, click into
the terminal and enter your first command, 'whoami' and press enter. 

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/1d4/c52/439/whoami.PNG"
class="fr-fic fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/1d4/c52/439/whoami.PNG?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/1d4/c52/439/whoami.PNG?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/1d4/c52/439/whoami.PNG?width=1920&amp;dpr=3 3x"
style="width: 492px;" />

It should return "root", which is the name on the Linux operating system
for the most powerful user on the system! On your journey through
hackerdom, you will learn to love "root" and all the power it gives you,
but for now, let's run a few more commands to see what is going on.

3\. Run the command 'echo "hello world" '. It will use the command
'echo' with the argument "hello world" to print to the screen. Hello
world is the classic programming introduction demo, so congrats on
officially making it!

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/ac7/798/ec3/1658453614618.jpg"
class="fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/ac7/798/ec3/1658453614618.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/ac7/798/ec3/1658453614618.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/ac7/798/ec3/1658453614618.jpg?width=1920&amp;dpr=3 3x"
style="width: 432px;" />

3\. Next, type the command 'ls' (like LS, but lowercase, then hit the
Enter key) to list all the files in the directory. <img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/0ff/f17/2d2/ls.PNG"
class="fr-fic fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/0ff/f17/2d2/ls.PNG?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/0ff/f17/2d2/ls.PNG?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/0ff/f17/2d2/ls.PNG?width=1920&amp;dpr=3 3x"
style="width: 459px;" />  

4\. Let's take that one step further now and add a flag to that 'ls'
command with 'ls -l'. (the -l is a lowercase L, not an i!)  The '-l'
flag allows you to see the long information printout for the files
listed. 

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/a08/5ad/a5d/1658453363362.jpg"
class="fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/a08/5ad/a5d/1658453363362.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/a08/5ad/a5d/1658453363362.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/a08/5ad/a5d/1658453363362.jpg?width=1920&amp;dpr=3 3x"
style="width: 487px;" />

  

5\. Now let's make a file of our own! Run 'echo "hello world" \>
newfile.txt'. This command will use the echo command to output the words
and then use the '\>' to redirect the words into a file we named. You'll
learn all about redirection and what we can do with that in this course,
but for now, create the new file and run 'ls -l' again.

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/5d8/79c/4d4/1658453725438.jpg"
class="fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/5d8/79c/4d4/1658453725438.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/5d8/79c/4d4/1658453725438.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/5d8/79c/4d4/1658453725438.jpg?width=1920&amp;dpr=3 3x"
style="width: 429px;" />

You should be able to see the new file and the updated time! (That time
is off because the Linux operating system these commands are running in
has their clock set to Coordinated Universal Time (UTC) but that is a
completely different subject we'll ignore for right now)

6\. There's a command named 'cat' on Linux which we can use to read
files from the terminal. Use 'cat newfile.txt' to read the file you just
created! <img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/2da/f8c/9c6/1658453988075.jpg"
class="fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/2da/f8c/9c6/1658453988075.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/2da/f8c/9c6/1658453988075.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/2da/f8c/9c6/1658453988075.jpg?width=1920&amp;dpr=3 3x"
style="width: 300px;" />

7\. Run the command 'ls -al'. The "-a" flag makes it so you can see all
files, and the "-l" flag allows you to see the long information printout
for the files listed. Combined, they create this view.

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/9fe/328/b62/1658453896209.jpg"
class="fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/9fe/328/b62/1658453896209.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/9fe/328/b62/1658453896209.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/9fe/328/b62/1658453896209.jpg?width=1920&amp;dpr=3 3x"
style="width: 447px;" />

Whoah! Now we can see a hidden file named ".ash_history". Linux hides
files with a . in front of them from the normal "ls", but you can find
them with "ls -a".

5\.  Let's use 'cat' to read the hidden file with 'cat .ash_history'. 

<img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/c26/784/d40/catash.PNG"
class="fr-fic fr-dib"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/c26/784/d40/catash.PNG?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/c26/784/d40/catash.PNG?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/c26/784/d40/catash.PNG?width=1920&amp;dpr=3 3x"
style="width: 522px;" />

Now we can see all the commands that we ran so far!!! 

Congratulations! In this brief series of commands, we have figured out
who we were, said hello to ourselves in a few ways, and found a hidden
file. That's pretty awesome! 

Honestly, you weren't supposed to understand everything (or anything)
you did there, but I promise, by the end of this course all of those
things will make sense.

  
