# Linux Permissions
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
Alright, we went over a little bit of this earlier, but let's dive into permissions. Permissions ***are*** security, and is one of the most important things that an OS provides.

We haven't put much time into it yet, but the OS basically segregates user and root process privileges using something known as "Protection Rings". 

[<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Priv_rings.svg/800px-Priv_rings.svg.png">](https://en.wikipedia.org/wiki/Protection_ring)

Even though rings 0-3 are shown, basically no major OSs use anything but Ring 3, Userspace and Ring 0, Kernel Mode. This is enough separation of powers for a level of protection to be given to the kernel by locking off userspace programs from accessing critical kernel functions. A very common misconception is that when you run as root, with ```sudo``` or otherwise, you are running in Ring 0. Not true! You are still in Ring 3 as a userspace process, albeit as UID 0 which gives you 'root' powers as granted by the configuration of the system. You will never transition to Ring 0 without control of a kernel mode driver (which is wildly out of scope of this course and 99.99% of jobs that require Linux).

Secure defaults and well-implemented permissions go a very long way towards making your Linux experience as smooth as it is. Userspace is all that really matters to us, so first, let's go over how permissions are represented, whether it is for the root user, background daemons, or everyday users.

# Basics

Run ```ls -l``` on a directory and look at the results.  Should look something like this:

```
drwxr-x--- 2 username groupname 4096 Jan 21 14:02 folder1
-rwxr-x--- 1 username groupname 15 Jan 21 14:02 file2
```

We went over this a bit earlier, but for old time's sake.

* The first bit tells us what type of file it is
  * "d" means directory
  * "-" means normal file
  * There are more options that can go here, but these are most of them
* The next 9 bits are permissions bits
  * This is what we are about to learn!!
* The next bit, a number, tells us how many hard links there are to the file, but don't worry about it
* The first name is the username who owns the file, in this case you
* The second name is the group who owns the file. Unless you've set up a group already, this should also be your username
* The next number is the file size in bytes
  * Directories are always the same size, but individual files should be listed as the number of bytes that make them up
* The next numbers should be the date and time last modified. These are not forensically accurate but are good enough to sort by timestamp.
* Finally, the name of the file you are looking at the details of

With that reviewed, let's dive into permissions. What do we do with these nine bits?

It's actually a sort of straightforward thing. The nine bits are split into three triplets that represent the perms (the cool way to say permission) for "User", "Group" and "Other".

> User    Group    Other
>  rwx      rwx      rwx
>  rwx      r--        ---
>  r-x       ---        ---

As you can see, these triplets are comprised of "r","w",and "x", which stands for read, write, and execute. Read means to access the file and read the bit stream, write means to modify the location in the drive, and execute means to run the process (assuming the file is an executable). The lack of permission to do one of those actions is represented by "-". This is constant across most OSs.

User and Group are defined by the names we see to the right of the permission bits when we run ```ls -l```. So if we see:
```
-rwxrw--- 1 jimmy students 15 Jan 21 14:02 file2
```
This means that the user 'jimmy' has read, write, execute perms, while the group 'students' only has read and write. Any user who is not in the group 'students' has no permissions whatsoever, not even to read the file.

We haven't made any groups in our VM yet, so most likely when you run ```ls``` you see your name for both user and group. That makes sense, don't worry about it.

[<img src="https://imgs.xkcd.com/comics/incident.png">](https://xkcd.com/838/)

# Modifying Permissions

Now things get fun, let's change some permissions around!

We use the command ```chmod``` and either "u" (for user), "g" (for group), "o" (for others), or "a" (for all 3) to do this on Linux. It's fairly straightforward, we either add ("+") or remove ("-") permissions with "r", "w", and "x". Here are some examples.

```
$ chmod g+x file2
> I bet you can guess what that does: add the executable bit to the group permission for file2. 
> Run ```ls -l``` again and you will see it has changed.
$ chmod g-w directory2
> Now we have removed the write bit for a directory2 for group.
$ chmod a+x file2
> Now we have added the executable bit for everyone.
```
We can use ```chmod``` to modify any permission on the file we own, as long as we have the permission to modify permissions. The most common use of ```chmod``` is when you download a file from somewhere, it is not given execute privs by default due to security policy. So anytime you find an executable not executing, you should check a chmod.

If we want to change permissions on something we don't own, you're going to need root access for that. Let's play around with changing ownership of files before we do that. Again, you'll need root access to change ownership.

```
$ sudo chown root file2
```

Now when we ```ls -l``` we see that file2 is owned by root. When the sudo command is finished running we drop back into our normal permissions (run ```whoami``` to check). If we try to change permissions now with ```chmod``` we will get a permission denied error. However, using ```sudo``` we can elevate privs again and ```chmod``` the permission around because we are the owner. This works for a file owned by any user, if you are root you can do what you want. It's good to be the king/queen.

Similar to ```chown``` is  ```chgrp``` which, you guessed it, changes the group. Basically the same usage as ```chown```.

A final thing we can do is set something known as "the sticky bit".

```
$ chmod +t file2
$ chmod +t directory2


```

This "+t" sets a file or directory as not-deletable by anyone other than the owner and root. This is great for shared folders.


# Bits and Permissions

Because of the magic of binary, if we have three bits, those bits can range from "111" to "000" which represents 7-0. This allows us to represent permissions as numbers as well.

* The read bit is "4"
* The write bit is "2"
* The execute bit is "1"

With three triplets, now our permissions look like this:

```
111 111 100
```
This is actually what the computer sees, so congratulations on finally getting inside the matrix. This is a big day!

Because we can add up the bits in binary, the "rwx" we were getting used to can also be represented by "111", "421", or "7". Lost yet? Keep thinking about this until it makes sense.

Now that you get it, this also allows us to set perms in chmod in a much cooler way.

```
$ chmod 755 file2

```

Damn that looks way more hardcore, you're using binary in real life. Look at you go. Adding up the bits lets us know which perms are on. All perms for everybody is represented by "777" but you should avoid doing that, it's the opposite of the Principle of Least Privilege.

You can also remove permissions by using lower numbers.  

```
$ chmod 744 file2

```

There we just removed the execute bit for group and others.

Assignment:

Using [these resources from the Security Fundamentals course]($@ASSIGNVIEWBYID*894@$), learn about Least Privilege. Discuss the Principle of Least Privilege and how it applies to file permissions in this format. 

```
 Answers:

 1.

 Resources:
 

 Pre-Questions:


 Post-Questions:


 Feedback:

```
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->