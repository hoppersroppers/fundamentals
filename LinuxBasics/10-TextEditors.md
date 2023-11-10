When we write programs, edit config files, or even take notes to study
later, we will do that with a text editor. Echoing and cating text only
gets you so far.

There are hundreds of text editors, and much like programming languages,
each has its own tradeoffs. Some are simple and have a GUI, some are
terminal only and are incredibly complex. Many have entire programming
languages built into them, or are even shells themselves, capable of
executing programs. As a general rule, use what works for you and don't
seek out complexity for complexities sake. I used to use the most
complicated text editor I could so I looked cool, now I use the simplest
ones I can for the job at hand.

Ubuntu comes with a few text editors installed initially, but the ones
we will focus on are gedit and vi/vim.

# gedit

To open Gedit, simply type `$ gedit &` in the terminal, or open it from
the GUI. gedit is a GUI application, and gives you a nice window, normal
use of your mouse, copy/paste, and all the normal things you expect from
a text editor, similar to Notepad on Windows. I use it all the time to
display information and make notes, but I also program in it every once
in a while.

Many people who like to think they are badasses think they are too cool
for gedit. Those people are silly and you should ignore anyone who
thinks that text editor choice has anything to do with how good of a
hacker you are.

# Terminal-Based Text Editors

gedit is a good option if you are on an Ubuntu desktop, but many times
you just won't have a GUI at all. If you are SSH'd into a box, or using
a server build, you will have to learn how to use a terminal text
editor.

# nano

The default editor that comes with most Linux distros is named `nano`.
It's basic, it's functional, and it gets the job done. To open it, type
`nano` and just start working. The keys to save and do other
functionality are displayed at the bottom, no tutorial needed. It's as
easy as it gets, it works great, and it's basically everywhere.

With that said, it doesn't really have any advanced features, so while
it's perfect for a minimal experience, if you're going to be coding you
likely want something more advanced (aka hardcore and hackerish).

# vi/vim

The other editor that comes with all Ubuntu distros is named `vi`. It
has a more modern, more advanced successor named `vim`. I think it is
better to initially learn vi/vim because it has more market share. Most
prominently, I often find myself using `vi` on computers I do not have
the ability to install new programs on. If I don't have the permissions
to `sudo apt-get install vim` or anything else, I am going to be using
`vi`, so it's easier for me to just use that for my terminal
text-editing needs. Because vi/vim are always available, I believe it is
the best family of editors to learn initially. You can always lean on
nano, but vi/vim gets the job done, better.

The final major terminal-based text editors is named `emacs`. Don't
worry about learning it, but it is good to know they exist. Notably,
there was once something named "The Editor Wars", when nerds argued with
each other if emacs or vim was better. Nobody won, everyone wasted time,
and if you hear anybody today talking about why one is better than the
other, ignore them. Even me.

![XKCD
Programmers](https://files.cdn.thinkific.com/file_uploads/429463/images/6a8/7bf/fdb/1629593920148.jpg)

What makes vi/vim/emacs/other terminal-based text editors special is
their extensibility and keyboard based shortcuts. By offering powerful
commands inside of the text editor, a programmer can speed up their
navigation of a code base and type faster.

vi and vim can be considered roughly equivalent when it comes to their
core shortcuts. To get an idea of how to work with `vim`, install it and
play around with the first few chapters of the built in tutorial by
running the command `vimtutor` from the terminal.

***Hint: To close out of vim, press escape key and type ":q". To save,
escape key then type ":w". Without that knowledge it can get a bit
awkward for beginners.***

However, the speed increase of mastering a cool text-editor is not
actually that much. Even if we increase speed of typing/navigation by
10%, it won't actually make us a better programmer. Luckily, there is a
form of text-editor that provides that benefit to us that we will talk
more about in the programming section. For now, vim should get us what
we need.

Play around with "vimtutor" and learn a few commands.

Print out a vim cheatsheet or put it on your desktop so that you can
constantly reference it. The more you use it, the easier it will be to
remember.

For your assignment, print out a cheatsheet or put it in your desktop if
you don't have a printer. Believe me, this is for your own good.
