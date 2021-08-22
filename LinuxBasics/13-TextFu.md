# TextFu
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
You've already done a little pipelining text-fu in the last section, so let's learn a few more commands that can be used to view and modify text streams. I'll give you some info about the commands, but in general, any time you want to learn more about these tools, just use the man pages.

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

```
Man Page Description: Remove sections from each line of files. Print selected parts of lines from each FILE to standard output.
```
The command ```cut``` does basically what you would expect it to, cut out parts of text. The way it works is we set a delimiter (-d) based off of what we want to split the file on. In this case, we use spaces, represented by " ". 

"-f" is used to describe what columns we want, numbered from the delimiter. We can also represent "1,2" as "1-2". Play around with cut to see what else you can do.

```
$ cat animals | cut -d " " -f 1,2
```
### awk

```
Man Page Description: The awk utility shall execute programs written in the awk programming language, which is specialized for textual data manipulation. An awk program is a sequence of patterns and corresponding actions. When input is read that matches a pattern, the action associated with that pattern is carried out.
```
The command ```awk``` is similar to cut, but assumes the delimiter is a space. using the brackets (your first bash script! Don't forget there is most of a programming language hidden in bash) we can choose to print however many items we want. Don't worry too much about how the variables (preceded by "$"" ) work, or how the script works, just send itttt.

```
$ cat animals |  awk '{print $1" "$2" "$3}'
```
### sed

```
Man Page Description: Sed is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline).
```

The command ```sed``` lets us do fancy targeted replacements of words using the format shown below. Play around with changing the words in the "/" to match different things.

```
$ cat animals |  awk '{print $1" "$2" "$3}' | sed 's/dog/anon/'
```

### tr

```
Man Page Description: Translate, squeeze, and/or delete characters from standard input, writing to standard output.

```
The command ```tr``` is an interesting one and allows you to do a direct swap of one character, or a range of characters to another. This is very useful for things like removing junk text or new lines (represented by "\n")
```
$ cat animals |  awk '{print $1" "$2" "$3}' | tr 'd' 'a'  
$ cat animals |  awk '{print $1" "$2" "$3}' | tr 'do' 'pi'  
```
### grep

```
Man Page Description: grep searches the named input FILEs (or standard input if no files are named, or if a single hyphen-minus (-) is given as file name) for lines containing a match to the given PATTERN. By default, grep prints the matching lines.
```

The ole' ```grep``` is crazy complicated but very powerful. One of my friends once wrote a 30 page book on how to use it effectively, but umm.... that's a little more than we need. Good for you though Danny boy.

95% of the time we need to use ```grep``` all we are using it for is to search for a string and then print the line the string is in to STDOUT. Combined with the many flags it has and ability to do complex searches, and piped into other commands it is exceptionally powerful. Check the manpage to see some of its other functionality.

```
$ cat animals | grep "dog"
```
### Bringing it all Together

Now on the /var/sys/log we looked at earlier, we can bring it all together. Let's say I hypothetically wanted to send you a copy of my /var/sys/log related to an issue about something named "systemd", but I didn't want you to know my username. What if we combined a bunch of these tools together to go through our logs and anonymize them for us. 

In this case I am using "dennis" in the script for name of the user I want to replace with "anon". If you don't know your username, run ```whoami```, to return the current user and put it into the script.

```
$ cat /var/log/syslog | grep "systemd" | awk '{print $3" "$4" "$5" " $10" "$11" " $12" "$13" "$14}' | sed 's/dennis/anon/'
```

Think about what just happened. For your assignment, write out what STDIN, STDOUT, and STDERR are and what is happening for each of the commands. (Hint: Don't forget about <https://explainshell.com/>, but be sure to fill in more of your answer using the man pages) Answer in the usual format.

```markdown
Questions:

1. grep
2. awk
3. sed

Resources:

0. Google
```
Respond in the usual format.
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
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->