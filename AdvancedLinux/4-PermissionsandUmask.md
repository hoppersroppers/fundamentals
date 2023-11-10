When a file is created in Linux, the default permissions for it is
"666". For a directory, the default permissions are "777". That is
basically always fine, but if you need to for some reason, you can
modify the default permissions using a command named `umask`.

# Masks

Okay, things are about to get a bit weird. You saw a little bit of
binary addition in the tutorial and hopefully that made some sense. Now,
you're going to learn about masks, which are a completely different
thing than binary addition. To avoid getting confused, keep in mind that
masks and binary addition have nothing to do with eachother, besides all
the 1s and 0s.

Masks are all over computing and generally can be defined as strings of
bits that set other bits based on logic. This logic is based on the
Digital Logic Gates we learned about in the "Digital Logic" section.

Depending on the required implementation, different logic gates can be
used for different masks. This means that the logic for a gate can be
"AND", "OR", "XOR"... long story short, don't think of masks as any
specific thing, just read what the logic is for that specific scenario
and reason about that in your head.

One of the more common uses of masks we see in Linux is for controlling
default permissions.

``` default
EX.
1  Binary:  6 6 6   // 110 110 110   
Mask:    0 2 2  // 000 010 010  
Output: 6 4 4 //  110 100 100 

EX.2  
Binary:  7 7 7 // 111 111 111  
Mask:    0 4 2 // 000 100 010  
Output: 7 3 5 // 111 011 101
```

Hopefully this makes sense. Honestly, you won't use this much, but it is
good to know about.

The most common place where you will see permissions masks is with the
`umask` command. Run it now and you will see what your shell's default
masks are.

Now make a new file and use `ls -l` to see what the permissions are. Do
they match?

In order to change your permissions that files default to for your
shell:

``` default
$ umask 002
```

This umask of "002" converts over to being a mask of "775".

When applied to This will change permissions so that files come out RWX
for user and group and R for other, but don't just believe me, test it
out.

You might have noticed that when you ran `umask` the first time there
was a leading "0" in front of the other numbers. That first bit is the
special bit we talked about earlier in terms of the "sticky bit". There
are other special types of files that can be indicated in the special
bit location, but don't worry about them for now.

For your assignment, discuss which bitwise operation is occurring when
the masks is applied. Answer in the appropriate format.
