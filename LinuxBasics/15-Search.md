# Search
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
## More Grep

We already played with ```grep``` a bit, let's do a little bit more. First, let's learn what grep stands for: Global Regular Expression Print.

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

If you only want to see the lines in the file which don't have the term you are greping for, use "-v".
```
$ grep -v "dog" animals
```

This defaults to showing line numbers and file names, so if you only want to see the filenames, use "-l".
```
$ grep -l "dog" animals
```

Play around with a few of the grep settings to see what else is possible, but don't worry about memorizing them, stick to cheatsheets. And as always, the manpages are your best friend!


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
> remember that / by itself searches from root (which is a whole lot of searching, so it takes a few minutes), while ./ only searches from current directory. Looks similar but very different results.
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
2. Write a command that finds any "hidden" (starts with . ) file in your user home folder.


Resources:

0. Google
```
Respond in this format.

```
 Answers:

 1.
 2.

 Resources:


 Pre-Questions:


 Post-Questions:


 Feedback:

```
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->