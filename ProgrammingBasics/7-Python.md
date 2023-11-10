It's time for you to learn your first programming language! Sort of! I
don't want to teach you programming as part of this course, it doesn't
fit into what I want to accomplish. 

What I want to accomplish is getting you exposure to things that will
open your mind to what is out there and give you the skills to get
things done, and the programming language Python is perfect for that.

![](https://files.cdn.thinkific.com/file_uploads/429463/images/4c5/305/f54/1654961982864.jpg)

Python is a programming language that has found incredible success,
largely due to the fact that code written in it is readable and things
just work. Programming is an exacting art, and Python doesn't force you
to work very hard to understand why things are the way they are. Other
languages, specifically C are better for learning the nitty-gritty,
which so far has been what this course focused on.

So why are we starting with Python? Simply, Python gets things done. It
just works. And for the beginning programmer, I don't want you to have
to worry about all the crap that other languages make you care about.
What I care about is you have the ability to do things, whether that is
automate your life or to crush CTF challenges.

While Python isn't the most popular programming language yet, it will be
in the next few years. It runs the backends of many giant companies, but
also is the dominant language for data science, and is the language of
choice for many people who need to move fast and get things done.
(That's us!)

Again, no language is perfect. There are tradeoffs with all languages,
some do better than others at various activities, some are worse. Python
is the most straightforward language to write code and do things with,
and has the best documentation examples for you to work off of. It is
considered to be "slow", but when people tell you that, ignore them and
continue writing your code. You will be done writing your program by the
time they start trying to troubleshoot why their program doesn't work.
Don't argue with people about programming languages, anyone who does
that for fun is the worst. Just let them have it.

# What is Python?

Python is a language developed primarily by Guido van Rossum, the
affectionately named 'Benevolent Dictator for Life'. He began work on it
in 1989 and since then thousands of people have contributed to the core
code base, and even more have written modules and extensions to allow
more to be done with the language. Potentially the most important design
consideration for the language was that it was developed to be highly
extensible, making it as easy as possible for people to build extensions
to allow programmers to use others' code in order to do more with less
lines of code.

Other aspects of the Python philosophy are:

-   Beautiful is better than ugly.
-   Explicit is better than implicit.
-   Simple is better than complex.
-   Complex is better than complicated.
-   Readability counts

Overall, Python is often described using the words: High level,
interpreted, dynamically typed, garbage collected, readable. For the
assignment you'll define those. Don't worry about what dynamically typed
means right now.

As a fun note, the language is named for Monty Python's Flying Circus, a
legendary British comedy show from the 70s. I really recommend you watch
some of their sketches, or the movie Monty Python and the Holy Grail.
It's on Netflix, but many of the sketches are on Youtube.

### Python Hello World

This might require some googling..... don't worry, that is how everyone
does it. You find something you need to do, and google how to do it.
Then you forget how to do it, and you go and google it again the next
time you do it. The next bit will help you set up your python
environment on Linux. Setting up environments is very time-consuming, no
matter what it is, but you will have to do this for basically every
language, and every version of each language, so you will have to get
good at it.

#### On Linux

Ensure the most up to date version of Python is installed on your Linux
box. Check this by running the command `python` from the command line.

If it responds with Python2 or the program is not installed, install a
modern Python version with
[https://docs.python.org/3/using/unix.html#on-linux](https://docs.python.org/3/using/unix.html#on-linux)

When you run `python` from the command line it brings up something
called an interpreter. The Python interpreter is neat because you can
use it to run programs one at a time.

With the interpreter open, do some basic math.

``` default
a = 2 
b = 3 
c = a + b 
print(c)
```

That should have printed c, which would have displayed as 5.

You can also print text from the interpreter. A program that prints
"Hello World!" to the screen is the classic first thing most tutorials
teach. Far be it from me to break with tradition, so here goes!

``` default
print("Hello World")
```

Make sure to have the quotes around the words that you printed. Don't
worry about what is happening right now, this is just to show what is
possible. To close out the interpreter, type `exit()`.

### Hello World

We used the interpreter, but you can only do very basic programs from
the interpreter, so usually you run python programs as their own files.

Python makes this incredibly easy in comparison to many other languages.

Here is the code:

``` default
print("Hello World!")
```

You might notice that as the same thing that the interpreter took as
input. Save it as "helloworld.py". ".py" is the python file extension.
It is just a text file, but the ".py" tells the OS what to do with the
file if you try to execute it.

Then, from the terminal, run that file you just created with:

``` default
$ python helloworld.py
```

Congratulations! Now you know how to program in Python! Sure, there are
a few steps between here and writing more complicated programs, but...
you'll get there!
