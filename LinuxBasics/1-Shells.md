# Shells
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
## Shells
In computing, a shell is a computer program which exposes an operating system's services to a human user or other program. It is named this because it  is the outer layer ("shell") around the OS, and any attempt to modify the OS goes through it. The way users modify the OS is by accessing either a Graphical User Interface (GUI) shell or a Command Line Interface (CLI) shell.

While the kernel is the base of the OS, the shell is what interfaces with it and is the most visible part of the OS.

## Graphical User Interface

We are most familiar with GUIs as that is what we use to navigate devices in our everyday life. Anytime we find ourselves using a mouse or a touch screen, or really find ourselves doing anything other than typing, we are using a GUI.

There are many different GUIs, with very different underlying software throughout the Linux ecosystem. This means that different versions of the same OS can have different appearances (or even the same appearance) without sharing the same code Another thing that is interesting to note about many Linux OSs is that some images ship without a GUI, especially images labeled for "servers". This means the OSs on these images can only be controlled from the command line. Early versions of Windows had the ability to run like this, but now all versions of Windows come with a GUI, even if it is not needed.

For an easy thing to do in Ubuntu, change the wallpaper to something cool. Do this through the GUI.


## Command Line Interface

The command line interface, or CLI, is a text based interface used to interact with the OS. When you think about hackers typing text into a black screen and running commands, they are operating with the CLI. Not only does it look really cool, it is also a very efficient way to run programs. For example, typing a few characters into the CLI can accomplish what 20 mouse clicks could do while operating through the GUI.

Both Linux and Windows have CLIs that we will be operating with as power users.

Linux:

* There are a variety of shells that exist in the Linux ecosystem, but the default is Bash (Bourne Again SHell) that we discussed in your Second Assignment.

Windows:

* CMD
  * A legacy interface that allows access to DOS commands
    * MS-DOS was the first Microsoft OS and contained many basic features that are still accessible via CMD
* Powershell
  * A fully featured interface and language that allows complex scripting via cmdlets and pipes. As the entire language was written for working with Windows, it allows fine grained control and easy manipulation of the OS.
* Windows Subsystem for Linux (WSL) - Windows 10 Only
  * The Windows Subsystem for Linux lets developers run a Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.
  * Basically, it's a mini-Linux VM, with access to all the same files on the host Windows machine.

We won't be doing much work with Windows in this course, so we will focus on learning the Bash Shell. For your first trick, open the shell by typing ctrl-alt-t, all at the same time.

 * Check to see your network settings by running the bash command "ifconfig"
 * Just doing that and leaving the terminal open in the corner makes you look like you know what you are doing, even if you learn nothing else from this course
 * You're welcome.

# Command Layout

When you run a command from the terminal, what occurs is that the shell will execute a program. However, we can modify the behavior of the program by adding what are called arguments. These arguments do things like configure settings, or tell programs to operate in a certain way, to do something and specify where to put it. To indicate an argument, we use something called a "flag" which says to the shell, hey, I am trying to modify the program that is running with the argument directly behind me. It looks something like this:

``` 
$ command -f argument
```

This command tells the shell to run the program "command" with the flag "-f" and the argument "argument". There can be dozens of flags and arguments to modify a command or how a program runs, so it gets complicated real quick. Luckily, we can use the ```man``` command to find out what exactly those flags and arguments do to modify the command. 

 For your next trick, we are going to modify your wallpaper entirely from the command line.

 First we have to download an image, and then we will use the command to make it our background.

```
$ wget -O /tmp/wallpaper.jpg "https://raw.githubusercontent.com/hoppersroppers/hoppersroppers.github.io/main/_layouts/constitution.jpg"
$ gsettings set org.gnome.desktop.background picture-uri file:////tmp/wallpaper.jpg
```

Now your background image should be a picture of a ship! If it didn't work, troubleshoot. If you're not on Ubuntu there is a very strong chance that you have a different default Desktop (Read: GUI) environment on your OS and it doesn't use 'gsettings'. Google around to figure out which Desktop environment you have and what you need to do to change your background from the command line.

## Assignment

```markdown
Questions:

1. Using the 'man' command, describe what the command using wget and the -O flag did
2. Using the 'man' command, describe what the command using gsettings did. If that didn't work, explain what you did to get it to work.

Resources:

0. Man
1. Google
```

Write up a few sentences for each of the questions. All of the answers are on this page, but ensure you answer any Pre-Questions you come up with.


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