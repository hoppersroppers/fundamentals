# Man Pages
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
So you've learned a few commands and you generally have an idea how to read manpages, but let's put you over the top. 

How do we learn about ```man```? Well, ```man man``` of course! 

There is a lot in there, but let's go through it piece by piece. 

```
MAN-PAGES(7)            Linux Programmer's Manual           MAN-PAGES(7)
```
> The top line here shows MAN-PAGES(7). What does the 7 mean? Well if we go a little bit further down we can see. 
```
NAME         top
       man-pages - conventions for writing Linux man pages
SYNOPSIS         top
       man [section] title
DESCRIPTION         top
       This page describes the conventions that should be employed when
       writing man pages for the Linux man-pages project, which
       documents the user-space API provided by the Linux kernel and the
       GNU C library....

   Sections of the manual pages
       The manual Sections are traditionally defined as follows:

       1 User commands (Programs)
              Commands that can be executed by the user from within a
              shell.

       2 System calls
              Functions which wrap operations performed by the kernel.

       3 Library calls
              All library functions excluding the system call wrappers
              (Most of the libc functions).

       4 Special files (devices)
              Files found in /dev which allow to access to devices
              through the kernel.

       5 File formats and configuration files
              Describes various human-readable file formats and
              configuration files.

       6 Games
              Games and funny little programs available on the system.

       7 Overview, conventions, and miscellaneous
              Overviews or descriptions of various topics, conventions
              and protocols, character set standards, the standard
              filesystem layout, and miscellaneous other things.
```
> MAN-PAGES defaults to the page which provides the documentation for how to write other manpages, which is filed under Section 7. 

Theres a ton more documentation underneath but we are going to ignore it right now because it isn't what we are looking for. We got the documentation guide but shouldn't the ```man``` we are looking for be in Section 1, as a user program? 

Let's try that command again, but instead specify Section 1.

```
$ man 1 man
```

There we go! Alright wow, lot going on there. We see the "MAN(1)" at the top, the name, a synopsis section that shows example usages, description, a bunch of usages... Alright that's enough, if we don't need to read the man page for something, don't! 

Let's look at something a bit more interesting. Use man to find the flag used to make ```mkdir``` "verbose". 

```
$ man mkdir
```

You should see the (1) in the top left so you know it's a command.

Verbose is just a fancy word for output more information to STDOUT and STDERR than usual, you'll see it all over the place. For many programs, adding a ```-v``` flag will really help with troubleshooting. 

Remember, if the man page doesn't help, googling the command and the word "usage" will usually get you where you need to be. 

Scroll to the bottom and you will see under "See Also" mkdir(2).

Go back to the command line with 'q' and check out the man page for the mkdir system call. 

Don't read it for understanding, just skim to see what this is showing. This task was meant to illustrate how system calls are defined so that software can make directories by using the OS provided API.  

You don't have to worry about system calls right now, just commands, but keep in mind that is what is going on behind the scenes for all the other software on your computer.
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->