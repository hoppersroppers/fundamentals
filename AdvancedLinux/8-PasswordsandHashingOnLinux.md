 [![](https://files.cdn.thinkific.com/file_uploads/429463/images/db7/d2f/a8a/1629595944831.jpg)](https://xkcd.com/538/)

A good deal of security is based around the idea of confidentiality,
that someone who is not authorized to read something can't read it. We
discussed the idea of permissions earlier, where someone who is not
authorized to read something is simply not granted access to it by a
computer, but there are situations in which we need to send or otherwise
expose sensitive data. To allow data to be exposed without
authentication, we need a way to protect that sensitive information from
people who don't know some sort of secret. This is where math comes in.

There are two primary ways to protect the confidentiality of secret
information: Encryption and hashing. Let's go into each a little bit,
but we will focus on hashing here.

### Encryption

Encryption is something you've definitely heard of before, it's the lock
on HTTPS websites, it's what we are supposed to do with sensitive files
before we send them via email, it's everywhere. Encryption, at it's
fundamental level, is doing math and having some sort of shared secret
between the sender and the receiver that any adversary who is listening
in doesn't have, so the sender can encrypt and the receiver can decrypt,
and the adversary doesn't know anything other than that a message got
sent.

There's a ton to learn about the study of encryption which is known as
cryptography, and I have a [giant section in my CTF course about
it](https://academy.hoppersroppers.org/course/view.php?id=7#section-5)
if you want to learn more.

## Encoding and Obfuscation

One big giant step down from encryption is encoding and obfuscation.
While they might look like encryption, they are really just ways of
translating data into another form. While you might need to spend some
time figuring out how it is obfuscated or encoded, there is no math
involved so it is far from secret.

Encoding is notably not always a security measure, and can be used to
get data into an acceptable format for transfer. One common example is
Base64 encoding, which can be used to convert a binary into printable
ASCII text.

## Hashing

Finally, we get to hashing, the star of this lesson. Hashing is what we
use if we wanted to encrypt something so that it could never be
decrypted again. What does that mean, you're probably thinking. Hashes
are designed to be mathematically one way, meaning it is impossible to
reverse a hash into the data that was used to create it. Hashing
functions are algorithms that take in any data, do math on it, and
output a string of some set length depending on the function, that can
be assumed to be unique to whatever the input was. To put it another
way, no two inputs should result in the same output hash (that doesn't
mean it's impossible, and it's very interesting when it does, but that
is outside the scope of this course).

Let's play around with hashing to try and get an idea of what this
means. One of the more famous hashing algorithms is md5, so we'll use
the 'md5sum' utility that should be included on your Linux machine.

Run this command, which takes the string "password" and gets the md5
hash of it.

``` default
$ echo "password" | md5sum
```

Now, run this command.

``` default
$ echo "password1" | md5sum 
```

As you can see, the outputs are completely different. As a sneaky note,
the echo command automatically adds a newline character to the end of
our input (so "password\\n" so that the terminal can display it
properly. This is a function of how terminals buffer text and display
things and it doesn't matter often, but in this case, it completely
changes our output because of how hashing functions work. To get the
actual MD5 hash of the string 'password', use echo's '-n' flag to remove
the trailing newline.

We can also use hashing on files and programs.

``` default
$ md5sum /bin/ls $ md5sum /etc/passwd
```

This will give us the unique hash of the 'ls' program or or /etc/passwd.
If a single bit in the program changes, the hash will be completely
different. This is used by many software companies when they distribute
software to verify the ***integrity*** of their software, as it allows
downloaders to verify the hash to make sure the file they received is
not corrupted. So hashing is interesting and one way, but doesn't that
mean everyone in the world who gets the md5 hash of "password" has the
same value? Absolutely. For a fun check, google the hash of 'password'
and you'll find that it is everywhere.

What does that mean then, that we can't use the password "password"
anymore because someone can view hashes, crack them using a dictionary
of common words, and then use it to log in? Well you shouldn't use
common words, but that's not actually much of a problem because of
something known as salting.

## Salting

Salting is a very cool technique where a computer or website creates a
unique string to place at the end of every password entered.This means
that they can leave their hashes publicly readable, but an attacker is
going to have a much harder time cracking them. Let's demo this, as if
we were a user setting their password for the first time on a system
with hashing enabled.

``` default
$ echo "password&secretsalt1337" | md5sum
```

So here we are emulating as if the user entered their new password
"password", the system added on a salt, in this case "&secretsalt1337",
and then the system saves the salt and the output of the md5 hash. The
original password entered will not be saved anywhere.

Now the next time when you enter your password, it will be combined with
the salt stored on file, hashed, and then the hash will be compared to
the hash on file, not any stored password. We'll come back to this
later, but it's 2021, there is no excuse to be storing someone else's
password.

## /etc/shadow

As we showed earlier, modern Linux versions don't store passwords in
/etc/passwd. Instead, they have been moved to /etc/shadow. So now, guess
we just have to `cat /etc/shadow` instead, right?

If you have been paying attention to this course so far, you probably
guessed that wouldn't work. If you check the permissions, in order to
read /etc/passwd, we need root access. So now we try it with superuser
privileges and we should see the results.

There should be a bunch of entries, but let's break one down.

``` default
dennis:$6$iU9KjTeD$5myyo4W7zppTOEdVUeP8/E6Kmjl7CtYYFqIIyes.fnNHy1fR0gJLb0q2KLhjAH6KrPpHZ0eJorBh.D74mq.vQ.:17952:0:99999:7:::
```

Briefly read through the man page for "shadow" and see the breakdown:
[man shadow](https://linux.die.net/man/5/shadow)

The most notable part of this is the password field, field \#2. To break
it out, we can see that it is represented by:

`:$6$iU9KjTeD$5myyo4W7zppTOEdVUeP8/E6Kmjl7CtYYFqIIyes.fnNHy1fR0gJLb0q2KLhjAH6KrPpHZ0eJorBh.D74mq.vQ.:`

Notably, you can't actually read the password! Let's break this field
down ever further:

-   $6
    -   This represents the hashing mechanism we are using to generate
        the hash from this password
-   $iU9KjTeD
    -   This represents the randomly generated salt used
    -   Remember how we were talking about salts earlier? In Linux, the
        salt is randomly generated for the user when they are created.
        These salts are different for each user.
-   $5myyo4W7zppTOEdVUeP8...
    -   This is the resulting hash of taking the user's password and the
        randomly generated salt

When a user types in a password, the OS takes the input, adds the salt
that is saved in /etc/shadow, hashes the string, and then compares the
output to the saved hash in /etc/shadow. If the hashes match, access is
granted.

So you might be asking, what is the salt for if an attacker can figure
out what it is, and then run a dictionary of common passwords against
it, to create a bunch of hashes, then compare those hashes to the hash
saved in /etc/shadow? Well, the answer is that it is super inefficient
to do that for every user. Without salts, attackers would only need one
giant list of hashes to check against. With salts, for every user they
need to run a new cracker against the hash. That is technically
difficult and expensive enough that very few attackers will ever take
the time to do that for your password. You're just not special enough,
which is a good thing.

Beyond this format, there are a few other characters that can be saved
in an /etc/shadow password field. The use of "!" or "\*" in this field
indicates that the account cannot be logged into using a password, and
must instead be logged into using an alternate method, such as an SSH
key. This minimizes risk by forcing an attacker to know or have
something besides a simple password.

As a note, on modern Linux systems there are a variety of authentication
methods (usually known as PAM) which use /etc/shadow in various ways.
They are outside of the scope of this course, if you ever find yourself
in a job that focuses on Linux auth, blame me for not teaching you
more... and then teach yourself.

## Lock or Delete an Account

If you need to lock an account so that it cannot be logged into, but
still exists, use this command.

``` default
$ sudo usermod -L account_name
```

It will modify the /etc/shadow file to have an "\*" in front of the
password field so the account cannot be logged into. Check this using
`cat`.

To delete an account:

``` default
$ sudo userdel account_name
```

# Assignment:

1.  What is in /etc/shadow? Describe how hashing, salting, and cracking
    work from the perspective of a defender.
2.  Break down this entry from /etc/shadow. Describe each field.
    especially focusing on the password field.
    -   `dennis:$6$iU9KjTeD$5myyo4W7zppTOEdVUeP8/E6Kmjl7CtYYFqIIyes.fnNHy1fR0gJLb0q2KLhjAH6KrPpHZ0eJorBh.D74mq.vQ.:17952:0:99999:7:::`
3.  Create an account, set the password, check the password in
    /etc/shadow. Then lock the account using `usermod`, check the
    password again. Now, unlock the account, you will have to Google or
    use man pages for this. Check /etc/shadow again. Briefly write up
    what you saw and any problems you had doing this.

Answer in the appropriate format.
