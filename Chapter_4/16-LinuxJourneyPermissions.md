Alright, we went over a little bit of this earlier, but let's dive into permissions. Permissions ***is*** security, and is one of the most important things that an OS provides.

Secure defaults and well-implemented permissions go a very long way towards making your Linux experience as smooth as it is. First, let's go over how permissions are represented.

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

# Modifying Permissions

Now things get fun, let's change some permissions around!

We use the command ```chmod``` and either "u" (for user), "g" (for group), "o" (for others), or "a" (for all 3) to do this on Linux. It's fairly straightforward, we either add ("+") or remove ("-") permissions with "r", "w", and "x". Here are some examples.

```
$ chmod g+x file2
> I bet you can guess what that does: add the executable bit to the group permission for file2. Run ```ls -l``` again and you will see it has changed.
$ chmod g-w directory2
> Now we have removed the write bit for a directory2 for group.
$ chmod a+x file2
> Now we have added the executable bit for everyone.
```
We can use ```chmod``` to modify any permission on the file we own, as long as we have the permission to modify permissions.

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

# Bits and Binary

I've been talking about bits a lot and kind of hand-waving them... but now it's time to double down and learn what bits are. In the process of learning bits, you will learn binary. Once you learn binary, you're a computer. Ipso facto, this is your last chance to stop before becoming a computer.

# Binary Basics

I'm going to be lazy here and recommend that you use this tutorial, it is fantastic and SparkFun is a great company.

Work through this tutorial: <https://learn.sparkfun.com/tutorials/binary>

Once you are done with that you're ready for what comes next.

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

Damn that looks way more hardcore, you're using binary in real life. Look at you go. Adding up the bits lets us know which perms are on. All perms for everybody is represented by "777" but you should avoid doing that, it's the opposite of the principle of least privileges.

You can also remove permissions by using lower numbers.  

```
$ chmod 744 file2

```

There we just removed the execute bit for group and others.

# Masks

Okay, things are about to get a bit weird. You saw a little bit of binary addition in the tutorial and hopefully that made some sense. Now, you're going to learn about masks, which are a completely different thing than binary addition. To avoid getting confused, keep in mind that masks and binary addition have nothing to do with eachother, besides all the 1s and 0s.

Masks are all over computing and generally can be defined as strings of bits that set other bits to 0.

For example:
```
EX.1
  Mask:   000 000 000
  Binary: 111 101 100
  Output: 111 101 100

EX.2
  Mask:   000 111 111
  Binary: 111 101 100
  Output: 111 000 000

EX.3
  Mask:   010 111 101
  Binary: 111 101 110
  Output: 101 000 010

```  

If a mask has a 1, the corresponding bit in binary is a 0, regardless of what it was before. Translating this over to numbers from binary we'll show a few more examples.

```
EX.4
  Mask:   0 7 7
  Binary: 7 5 4
  Output: 7 0 0

EX.5
  Mask:   2 7 5
  Binary: 7 5 6
  Output: 5 0 2

```  

Hopefully this makes sense.

The most common place where you will see permissions masks is with the ```umask``` command. Run it now and you will see what your shell's default mask is.

Now make a new file and use ```ls -l``` to see what the permissions are. Do they match?

In order to change your permissions that files default to for your shell:

```
$ umask 002
```

This will change it so that files come out RWX for user and group, but don't just believe me, test it out.

You might have noticed that when you ran ```umask``` the first time there was a leading "0" in front of the other numbers. That first bit is the special bit we talked about earlier in terms of the "sticky bit". There are other special types of files that can be indicated in the special bit location, but don't worry about them for now. 
