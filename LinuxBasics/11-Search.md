More Grep

We already played with `grep` a bit, let's do a little bit more. First,
let's learn what grep stands for: Global Regular Expression Print.

``` default
$ cat animals | grep "dog" $ grep "dog" animals
```

Both of those do the same thing. We can also search an entire directory
by using the "\*" symbol, often known as a wildcard. This wildcard will
open every file in a directory.

``` default
$ grep "dog" *
```

As a note, you can also `cat *` in case you ever want to print every
file in a directory. Many other commands use the wildcard operator.

If you only want to know which files in a directory have the target
word, use "-l".

``` default
$ grep -l "dog" *
```

If you want to know the file name and line number, use "-n".

``` default
$ grep -n "dog" *
```

If you only want to see the lines in the file which don't have the term
you are greping for, use "-v".

``` default
$ grep -v "dog" animals
```

This defaults to showing line numbers and file names, so if you only
want to see the filenames, use "-l".

``` default
$ grep -l "dog" animals
```

Play around with a few of the grep settings to see what else is
possible, but don't worry about memorizing them, stick to cheatsheets.
And as always, the manpages are your best friend!

## find

Alright, last command for the search section! While `grep` cared about
searching through files, `find` only cares about file information!

Here are some example uses of `find`. There are a ton of flags for this,
so use man anytime you need to do look for something you don't know the
flags for

``` default
$ find directoryName -name secret 
> find all files named secret in a folder named directoryName 
$ find directoryName -type f -name "*.txt" 
> find all .txt files. Note the "*" wildcard 
$ find directoryName -type f -perm 0777 -print 
> find all files with the permission 0777. Don't worry too much about permissions yet. 
$ find directoryName -type f -name ".*" 
> find all secret files! The "." in front of the filename hides it from a standard ls. 
$ find / -user dennis 
> find all files from the root directory owned by the user dennis 
> remember that / by itself searches from root 
(which is a whole lot of searching, so it takes a few minutes)
 while ./ only searches from current directory. 
Looks similar but very different results. 
$ find / -size 50M 
> find all files from root that are 50MB 
$ find / -mtime 5 
> find all files modified in the last 5 days. 
Kind of useful from a forensics standpoint, though timestamps are unreliable!
```

This ain't everything but should be enough to help.

## Assignment

``` default
Questions:
1. Write a command that will find all .html files on a computer that are 12 bytes in size, owned by "jake". 
   * You can make an example file by putting the contents "is this html" into a file and saving it as a .html file. 
   * However, getting the owner to be named Jake would require you to create a new user on your system and that is a bit of work
   * I recommend you just write one that will find ones owned by you, and then for your answer, submit the "Jake" version.
2. Write a command that finds any "hidden" (starts with . ) file in your user home folder.

Resources:
0. Google
```
