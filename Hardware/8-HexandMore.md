# Hex and More

<iframe allowfullscreen class="fr-draggable" height="360" src="https://www.youtube.com/embed/DWge4-gMdLk?wmode=opaque" width="640"></iframe> 

We've talked about enough hardware, but let's go back to the people side
of computing. All things considered, you can avoid binary and worrying
about CPU stuff most of the time, so let's not focus on them too hard or
be too freaked out it is really complicated. If your job is going to
require that, you can get good at it.. otherwise... move on.

You've gotten a taste of binary, let's talk about non-binary
representation. 1s and 0s really are hard to read, so luckily we have
something a bit more 68756d616e207265616461626c65... sorry, human
readable. Hexadecimal, base 16, hex, whatever you want to call it, will
become a language that you see constantly during your technical journey.
Being comfortable working with hex is one of the skills that will help
you stand out.

From the same site as the binary tutorial (gee, sure hope you liked it)
we have an introduction to hexadecimal.
<a href="https://learn.sparkfun.com/tutorials/hexadecimal"
rel="noopener"
target="_blank">https://learn.sparkfun.com/tutorials/hexadecimal</a>

Now, back to the terminal.

``` default
$ echo "Hello!" > file4 $ xxd file4
```

xxd is able to convert a file into its hexadecimal representation. If
you do not have it installed, install it with apt-get.

Download this image using wget or curl: <a
href="https://raw.githubusercontent.com/hoppersroppers/hoppersroppers.github.io/main/_layouts/compass.png"
rel="noopener"
target="_blank">https://raw.githubusercontent.com/hoppersroppers/hoppersroppers.github.io/main/_layouts/compass.png</a>

Open the file with xxd and check out what is in it. Shouldn't make much
sense, but it should at least look cool.

File formats (and networking protocols, and all sorts of other things on
the internet) are defined in documents known as RFCs. All files follow
the rules for their file format.

Read through the .png format RFC and find where the file signature, aka
the "magic number" is defined. Don't even think about reading the whole
specification, just look for what you need and move on!

<a href="https://tools.ietf.org/html/rfc2083" rel="noopener"
target="_blank">https://tools.ietf.org/html/rfc2083</a>

Nobody has this content memorized, but when they deep dive into a format
or protocol, the RFC has the answers. You'll spend plenty of time
looking through RFCs, but not right now. It makes your brain hurt.

Any time you need to deal with a file format, google/wikipedia will
provide most of the answers. If you need to dig deeper than that, go to
the RFC.

# Hex-editing

`xxd` is not really a hex-editor, it just displays hex. However, we can
use it to convert files into hex, make edits to them with our favorite
text editors, then convert the files back into the correct formats.

First, let's make a copy of the .png you downloaded using `cp` and name
it "copyOfPng.png"

We can then use `xxd` to convert the file into a hexdump.

``` default
$ xxd copyOfPng.png > hexDumped
```

Now if we open hexDumped with our text editor of choice we can see that
it is in a new format. Make an edit to the file and change the first
four characters (the magic numbers) to be 0000. Save your changes and go
back to the terminal.

Now we will use `xxd` to rebuild the file from hex.

``` default
$ xxd -r hexDumped > modified.png
```

Try to open modified.png. It shouldn't be opening now because we mangled
(that's a technical term for corrupted) the file header!

# diff

One useful tool to find the difference between files is to use `diff`.
diff takes two pieces of text and compares them, looking for
differences. With text files usage is as simple as
`$ diff file1.txt file2.txt` and the results will display.

It is slightly more complicated with binary files or other dense formats
like images. To see what the difference between the original image and
the new mangled file we were playing with before:

``` default
$ diff -y <(xxd copyOfPng.png) <(xxd modified.png)  
```

Little bit of fancy footwork going on with redirectors here!!!! We are
converting the images to hex with xxd, then redirecting them, then using
them as arguments for the diff command.

This will display the differences between the two files. `diff` is
great, you will use it all the time. There are GUI versions of diff, but
I also really like using online ones in browsers. Saves some time when
you need it, and usually very good. I recommend
<a href="https://www.diffchecker.com/" rel="noopener"
target="_blank">https://www.diffchecker.com/</a>.

To fix this mangled file header, we will use a hex-editor. Hex-editors
do a similar thing to xxd, but also give us the ability to edit in a
nice GUI. The one we will use is `bless`. It is not particularly fancy
but it gets the job done. To install:

``` default
$ sudo apt-get install bless
```

To open up the mangled file, run `$ bless modified.png`. Now, using the
RFC, correct the mangled bits on the front so that you are able to open
the image again.

## Base64

Base64 is another encoding scheme that uses, you guessed it, 64
characters to represent data in an ASCII text format. Base64 is commonly
used to encode binaries that would not be able to be sent via methods
that only use ASCII, such as in HTML, in URLs, or in some email formats.

Base64 is visually distinctive because of its use of "=" at the end of a
string of letters and numbers. Most of the time when you see that form,
it will be Base64, simply based off of how common Base64 is. Don't worry
too much about why there is an "=" sign, it is for padding to make
translation easier.

To manipulate Base64 in the terminal, we use the command `base64`.

``` default
$ echo "Hello World" | base64 
$ echo "Hello World" > 64dText $ base64 --decode 64dText 
$ base64 --decode SGVsbG8gV29ybGQ=
```

It isn't often that you have to do this from the command line, but it
happens occasionally.

For this assignment, I am going to have you convert between encodings by
hand. This is meant to ensure you understand what is going on. Don't
cheat, and don't move on until you get it, this is very important you
understand.

Assignment:

1.  Alright. Now. Convert 17 in Ascii to Binary and Hex. Do it by hand.
2.  Convert "Go Navy" to Octal, Hex, and Binary. Yes. By hand. Use
    Google to figure out how. This is supposed to not be fun.
3.  What does "c2l4dHlmb3Vy" translate to from Base64?

It is annoying to do that by hand, but it does help in the long run. ...
but here is a tool so that you never have to do that again as my apology
for making you do it.
<a href="https://gchq.github.io/CyberChef/" rel="noopener"
target="_blank">https://gchq.github.io/CyberChef/</a>.

Fun fact, it is released by GCHQ, Britain's version of the NSA. Great
tool and very useful for converting encodings/encryption, but there is
so much more. There are about a thousand uses for this thing and many
security professionals use it all the time. I love it for CTFs.
