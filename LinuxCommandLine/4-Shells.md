# Shells

Both Linux and Windows have CLIs that we will be operating with as power
users.

Linux:

-   There are a variety of shells that exist in the Linux ecosystem, but
    the default for many OS's is known as Bash (Bourne Again SHell).
    You'll be best friends with this eventually.

  

Windows:

-   CMD
    -   A legacy interface that allows access to DOS commands
    -   MS-DOS was the first Microsoft OS and contained many basic
        features that are still accessible via CMD
-   Powershell
    -   A fully featured interface and language that allows complex
        scripting via cmdlets and pipes. As the entire language was
        written for working with Windows, it allows fine grained control
        and easy manipulation of the OS.
-   Windows Subsystem for Linux (WSL) - Windows 10 Only
    -   The Windows Subsystem for Linux lets developers run a Linux
        environment -- including most command-line tools, utilities, and
        applications -- directly on Windows, unmodified, without the
        overhead of a traditional virtual machine or dualboot setup.
    -   Basically, it's a mini-Linux VM, with access to all the same
        files on the host Windows machine.

We won't be doing much work with Windows in this course, but for your
first trick, open the shell by typing "cmd" and enter into the Windows
search bar. 

-   Check to see your network settings by running the command "ipconfig"
-   Just doing that and leaving the terminal open in the corner makes
    you look like you know what you are doing, even if you learn nothing
    else from this course
-   You're welcome.

# Command Layout

1\. Visit this online shell: <a
href="https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&amp;mem=192"
rel="noopener noreferrer" target="_blank">JS Linux Browser Shell</a>

2\. Once it has loaded, use the command "ls" to list all the files in
the directory. 

3\. Use the command "cat readme.txt" to read the contents of the file in
"readme.txt". 

4\. In that file you will find 3 more commands to run. 

5\. Use "cat hello.c" to read the contents of hello.c. What do you
expect to happen?

6\. Use the first command in readme.txt  "gcc hello.c -o hello" to
create an executable named hello

7\. Use "ls" to verify the creation of the new file.

8\. Use the command "./hello" to run the new file

  

Congratulations! In this brief series of commands, we have navigated a
new system, found a file written in a programming language named C,
turned that file into an executable program, and ran it! That's pretty
awesome!

Honestly, you weren't supposed to understand everything you did there,
but hopefully you feel very cool! Don't worry about pre-questions for
this section.

Assignment

``` default
Questions:
1. In your own words, describe what the command 'ls' does
2. Describe what the command 'cat' does
3. Describe what the command using 'gcc' does
4. Describe what the program ./hello did

Resources:
0. Man Pages
1. Google
```

Write up a few sentences for each of the questions. 
