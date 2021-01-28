# TextFu

You've already done a little pipelining text-fu in the last section, so let's learn a few more commands that can be used to view and modify text streams.

Let's start with viewing, because that is pretty straight forward.

## Viewing Streams

In addition to the wonderful ```cat``` we also have:

* head
  * head will print the top few lines of a larger file
* tail
  * tail will print the last few lines of a file
* less
  * less will bring you to the top of a file and allow you to scroll or search through it
  * more exists but is "deprecated", which means you shouldn't use it but it probably still sort of works

  For a good sized file to test these on use ```/var/log/syslog``` as your target. Don't worry too much about what is going on with the file path you just chose, we'll talk about it more in the File Systems section. The takeaway here is knowing which to use when looking at a large file.

  If you try to ```cat``` your syslog you will see something I call runaway prints and it will fill up your terminal. Type ```clear``` to clear it on out. If you find that you've broken your terminal and things aren't displaying properly, type ```reset```.

## String Modification

Let's learn some more tools to work with files. Hopefully you still have your animals file from last section, otherwise make it again. I'll give you some commands, play around with them and read the manpages to get an idea what else they can do besides the basic functionality.

### cut
The command ```cut``` does basically what you would expect it to, cut out parts of text. The way it works is we set a delimiter (-d) based off of what we want to split the file on. In this case, we use spaces, represented by " ". "-f" is used to describe what columns we want, numbered from the delimiter. We can also represent "1,2" as "1-2". Play around with cut to see what else you can do.

```
$ cat animals | cut -d " " -f 1,2
```
### awk
The command ```awk``` is similar to cut, but assumes the delimiter is a space. using the brackets (your first bash script! Don't forget there is most of a programming language hidden in bash) we can choose to print however many items we want. Don't worry too much about how the variables (preceded by "$"" ) work, or how the script works, just send itttt.

```
$ cat animals |  awk '{print $1" "$2" "$3}'
```
### sed

The command ```sed``` lets us do fancy targeted replacements of words using the format shown below. Play around with changing the words in the "/" to match different things.

```
$ cat animals |  awk '{print $1" "$2" "$3}' | sed 's/dog/anon/'
```

### tr
The command ```tr``` is an interesting one and allows you to do a direct swap of one character, or a range of characters to another. This is very useful for things like removing junk text or new lines (represented by "\n")
```
$ cat animals |  awk '{print $1" "$2" "$3}' | tr 'd' 'a'  
$ cat animals |  awk '{print $1" "$2" "$3}' | tr 'do' 'pi'  
```
### grep

The ole' ```grep``` is crazy complicated but very powerful. One of my friends once wrote a 30 page book on how to use it effectively, but umm.... that's a little more than we need. Good for you though Danny boy.

95% of the time we need to use ```grep``` all we are using it for is to search for a string and then print the line the string is in to STDOUT. Combined with the many flags it has and ability to do complex searches, and piped into other commands it is exceptionally powerful. Check the manpage to see some of its other functionality.

```
$ cat animals | grep "dog"
```
### Bringing it all Together

Now on the /var/sys/log we looked at earlier, check out all the fun things we are doing. As a hint, if the person who is running this command types ```whoami```, "nameofuser" is what is returned.
```
$ cat /var/log/syslog | grep "auth" | awk '{print $3" "$4" "$5" " $10" "$11" " $12" "$13" "$14}' | sed 's/nameofuser/anon/'
```

Think about what just happened. For your assignment, write out what STDIN, STDOUT, and STDERR are and what is happening for each of the commands. Answer in the usual format.

```markdown
Questions:

1. cat
2. grep
3. awk
4. sed

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

________________


# Search

## More Grep

We already played with ```grep``` a bit in the last section, let's do a little bit more. First, let's learn what grep stands for: Global Regular Expression Print.

```
$ cat animals | grep "dog"
$ grep "dog" animals
```
Both of those do the same thing. We can also search an entire directory by using the "*" symbol, often known as a wildcard. This wildcard will open every file in a directory.
```
$ grep "dog" *
```
As a note, you can also ```cat *``` in case you ever want to print every file in a directory. Many other commands use the wildcard operator.

If you only want to know which files in a directory have the target word, use "-l".

```
$ grep -l "dog" *
```

If you want to know the file name and line number, use "-n".
```
$ grep -n "dog" *
```

If you only want to see files which don't have the term you are greping for, use "-v".
```
$ grep -v "dog" animals
```

This defaults to showing line numbers and file names, so if you only want to see the filenames, combine "-v" and "-l".
```
$ grep -v -l "dog" animals
```

## regex

So far I've only shown you the exact match operator which uses parentheses, but grep has the ability to do many other forms of pattern matching described in the manpage. One of the most useful is regex. Regex stands for "Regular Expression" (hey remember that from the grep acronym?) Regular expressions are a technical way to define a particular search pattern, and grep is built around them.

While we have only done "literal" matches so far, regex is crazy complicated and basically a programming language in itself. I'd love to try and teach you, but learning regex is a course in itself. Anytime you need to use it, pull up a helpful site like this [regex tester](https://regex101.com/) and get your regex query working on some test data.

I highly recommend Google and specifically Stack Overflow results for regex help, very often someone else has already done 75% of what you are trying to accomplish.

## find

Alright, last command for the search section! While ```grep``` cared about searching through files, ```find``` only cares about file information!

Here are some example uses of ```find```. There are a ton of flags for this, so use man anytime you need to do look for something you don't know the flags for  

```
$ find directoryName -name secret
> find all files named secret in a folder named directoryName
$ find directoryName -type f -name "*.txt"
> find all .txt files. Note the "*" wildcard
$ find directoryName -type f -perm 0777 -print
> find all files with the permission 0777. Don't worry too much about permissions yet.
$ find directoryName -type f -name ".*"
> find all secret files! Remember the "." in front of the filename hides it from a standard ls.
$ find / -user dennis
> find all files from the root directory owned by the user dennis
$ find / -size 50M
> find all files from root that are 50MB
$ find / -mtime 5
> find all files modified in the last 5 days. Kind of useful from a forensics standpoint, though timestamps are unreliable!
```

This ain't everything but should be enough to help.


## Assignment

```markdown
Questions:

1. Write a command that will find all .html files on a computer that are 12 bytes in size, owned by "jake".
2. From that command, write the regex that will only select files with a string in it that matches the format:
  * any character, any number, case insensitive letter D, lowercase v, !.
  * Ignore all "," and " "" in that description for your actual regex
  * Example strings that would match this are:
    * s3Dv!
    * !0Dv!
    * 42Dv!
3. Combine the last two questions to write a command that does everything required in the first question, and prints the line of any file that matches the regex. 
3. What does alphanumeric mean?

Resources:

0. Google
```
Respond in this format.

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
