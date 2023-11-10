So far I've only shown you the exact match operator for grep which uses
parentheses, but grep has the ability to do many other forms of pattern
matching described in the manpage. One of the most useful is regex.
Regex stands for "Regular Expression" (hey remember that from the grep
acronym?) Regular expressions are a technical way to define a particular
search pattern, and grep is built around them.

As an aside, Regex is everywhere in computing. You can use it for HTML
input validation, you can use it to search for data in log files,
basically anytime that a standard exact string search won't help. It is
implemented in most text editors and programming languages. Regex is
very complicated, very powerful, and basically a programming language in
itself.

To make things even more complicated, [there are multiple competing
regex
syntaxes](https://en.wikipedia.org/wiki/Regular_expression#Standards),
all of which are slightly different. Any time you find yourself doing
regex, make sure to check which standard is being complied with and
modify your regex accordingly. Posix and Perl standards, despite both
starting with p are NOT the same!

I'd love to try and teach you, but learning regex is something I don't
wish on anyone, and more importantly, you don't need to learn regex...
or even understand it.

As a famous hacker once said:

"Some people, when confronted with a problem, think "I know, I'll use
regular expressions." Now they have two problems.

We will go over some quick examples, but don't plan on leaving this
section an expert on Regex, more just be confident you can deal with it
if you need to. You won't use it often enough to justify the headache of
"learning" it, I promise.

First, read this blog on ['The Absolute Bare Minimum Every Programmer
Should Know about Regular
Expressions'](https://web.archive.org/web/20090209182018/http://immike.net/blog/2007/04/06/the-absolute-bare-minimum-every-programmer-should-know-about-regular-expressions/).
It is considered by many to be the best regex intro on the internet.

### Example 1: Cheatsheet

Now that you've read that and have a vibe, let's get into it. Here is a
cheatsheet (<https://www.rexegg.com/regex-quickstart.html>) which should
give you everything you usually need to figure out Regex stuff. The hard
part is tying all the things on this cheatsheet together.

Look through these examples from
[https://cs.lmu.edu/\~ray/notes/regex/](https://cs.lmu.edu/~ray/notes/regex/)
to get an idea of how regex works:

-   gr\[ae\]y = contains {gray, grey}
-   b\[aeiou\]bble = contains {babble, bebble, bibble, bobble, bubble}
-   \[b-chm-pP\]at\|ot = contains {bat, cat, hat, mat, nat, oat, pat,
    Pat, ot}
-   z{3,6} = contains {zzz, zzzz, zzzzz, zzzzzz}
-   z{3,} = contains {zzz, zzzz, zzzzz, ...}
-   \\d = contains {0,1,2,3,4,5,6,7,8,9}
-   \\d+(.\\d\\d)? = contains a positive integer or a floating point
    number with exactly two characters after the decimal point.
-   1\\d{10} = contains an 11-digit string starting with a 1
-   ^dog = begins with "dog"
-   dog$ = ends with "dog"
-   ^dog$ = is exactly "dog"

Now, if we were going to write a regex to find all matches that started
with a number, had a space, a 3 letter word, and ended with another
number, we can try to write that out.

Starting with "a number": \\d

Then "a space" \\s

Then, "a 3 letter word": \\w{3}

Finally, "ends with another number": \\d$

To bring it all together, the regex would be "\\d\\s\\w{3}\\d$".

But how do we know we did it right?

### Example 2: Regex101

You know to use the cheatsheet, but how do you nail down your Regex to
be sure you are getting all the results? Anytime you need to do
something complicated, pull up a helpful site like this Regex tester
([https://regex101.com/](https://regex101.com/)) and get your regex
query working on some test data.

For the query you just wrote, open up Regex101 and enter it into the top
line.

Then type out a couple of examples of strings you want the regex to
match and not match, for example:

``` default
3 dfs2 3ddd3 1 d3d 2 3ed3 a aaa1 423aa2
```

When you enter them into the tester you will see which ones work and
which don't, which will allow you to edit as required.

There is even a helpful Explanation and Quick Reference section to help
you write even more complicated queries.

### Example 3: Google

With the cheatsheet and a Regex tester, you've got most of what you
need. In addition, I highly recommend Google and specifically Stack
Overflow results for regex help, very often someone else has already
done 75% of what you are trying to accomplish. Then you can take that
result, put it into the Regex tester, and fiddle away until it works.
Again, not trying to make you an expert, just good enough.

For example, what if someone tells you to write a regex to look for
email addresses? Well... \* First we think letters and numbers,
separated by an @ sign, with a domain, a period, and then the tld at the
end... \* But what about all the other symbols? Turns out most symbols
work in the name too "!#$%&'\*+-/=?^\_\`{\|}\~" (though you will mostly
only see '-'). \* And then also '-' are allowed in domains, so those can
be in the back half as well.

So these are all valid:

-   very.common@example.com
-   "very.(),:;\<\>\[\]\\".VERY.\\"very@\\
    \\"very\\".unusual"@strange.example.com
-   admin@mailserver1

How do we solve this seemingly difficult task?!? Read the email RFC?
Wikipedia?

How about google for a regex that matches emails?

[https://stackoverflow.com/questions/201323/how-to-validate-an-email-address-using-a-regular-expression](https://stackoverflow.com/questions/201323/how-to-validate-an-email-address-using-a-regular-expression)

Hell to the yeah.

Don't worry, this shouldn't have made sense, and you should feel like
you don't understand regex at all. That is perfectly normal. Struggle
through this assignment using the tools and tips I have given you, and
then move on with your life.

## Assignment

Make sure you know what type of Regex standard you are using!!!! If it
seems like some options don't exist, you might be crossing
syntaxes/interpreters!

Questions: 
