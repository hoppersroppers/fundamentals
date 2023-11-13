# Git Hello World

## Open Source

You might have heard of Open Source before, as there has been an
infinite amount written about the subject, but this is a good time to
learn about it. In fact, this course is entirely open source!

Open source and hacking go hand in hand. You might not feel strongly
about it now, but you probably will eventually.

What is Open Source?
<a href="https://opensource.com/resources/what-open-source"
rel="noopener"
target="_blank">https://opensource.com/resources/what-open-source</a>

## Git

Before we get to Github we have to learn about the software it is built
around, which is named 'git'. Git was developed by…. drumroll… Linus
Torvalds! Basically, once he started working on Linux with a bunch of
other programmers, he needed a dedicated type of software so everyone
could work on different pieces without stepping on each other's toes.
What was created is something now known as a “version control system” or
VCS.

There are a variety out there, but Git is clearly dominant. Git is used
for version control during software development, allowing collaboration
and the merging of changes in a safe and easy manner. It is used by just
about everyone and is amazing. If you want to build large pieces of
software, especially as a group, you need to use version control.
However, as you’re about to find out, git can be a bit of a beast to
manage.

## Github

Luckily, some helpful folks decided to add features to git that old
Linus would have never agreed to, and now we have Github. Github is a
website that wraps git and allows you to share your code via their
website, as well as letting you download other people's code. It’s The
Place for sharing the source code of your digital creations with the
world, and checking out what others have written.

## Repositories

The way git works is by manipulating things named “repositories” or
“repos”. By keeping track of all the code, and all the changes to the
code over time, git is able to show snapshots of what the code looks
like at different points. Inside of each repo there can be multiple
“branches” which git will also keep track of. This means that different
programmers can be working on different branches inside of one repo, and
then “commit” their changes to the main branch. The git software will
keep verify nothing conflicts, keep track of who did what when, and then
“merge” all the code together. We can host our git repos locally or
somewhere in the cloud. The primary objective of Github is to be that
remote location to store git repos. Github and git knowledge is
basically required for any programmer job, so let’s do a quick lab to
drive home how that works.

# Tutorial

First, make a github account at
<a href="https://github.com/" rel="noopener"
target="_blank">https://github.com</a>

Then ensure git is installed on your computer with "git status". If it
is not, install git.

Once you have verified that you have git on your computer and made a
Github account, it is time to 'fork' my repository
<a href="https://github.com/hoppersroppers/demoHtml" rel="noopener"
target="_blank">https://github.com/hoppersroppers/demoHtml</a>. Forking
is the cool programmer word for making a personal copy of a repo.

There are multiple ways you can do this, but the way we will do it here,
will combine the Github Web Interface and some CLI action. First, "fork"
<a href="https://github.com/hoppersroppers/demoHtml" rel="noopener"
target="_blank">https://github.com/hoppersroppers/demoHtml</a> via the
Github website by clicking the fork button in the top right.  Now you
can refer to your repo as a fork of mine, which honestly sounds cool,
plus it makes sense! 

Now, let's clone your fork to your computer.

``` default
$ git clone https://github.com/---yourUserName---/demoHtml
```

This will make a local copy of your fork on your computer. Keep in mind,
this is not considered forking your fork, simply cloning. Check that the
repo downloaded with `ls` and then cd into it.

### Files in the Git Repo

Use `ls` to see what is in the directory. You should see hello.html,
README.md, and a LICENSE.

-   README.md is the common name of the file used to understand what is
    going on in the repo. If you visit your repo you forked you will see
    that the README is displayed to you when you click in.

-   LICENSE is the common filename of the Open Source license the file
    is released under. There is a ton of complexity in this that is
    basically copyright law, so for now don’t worry about it, but just
    know that it is important to check these out before blindly taking
    someone else’s code and using it in your work. You can click to your
    Repo in Github to see what the License is in the top line.

-   Finally we have hello.html. It’s a regular HTML file which is the
    language websites are built with. We can render it in our browser by
    opening it and selecting our browser as the correct program. We can
    also edit it by selecting a text editor to open it, liked gedit or
    one of our command line options. If you've ever looked at "View
    Source" in your browser before, you were looking at HTML.

### Editing Our First File

First, run `git status` to check out how everything is going. If you get
errors, figure them out before moving forward... as I like to say, the
best time to fix merge issues is before you find out about them. 

status will tell you right now that you are in branch "main". "main" is
the default branch name for a Github repo. It is possible to switch
branches and have different changes in each branch, but for now,
everything we will do is in main.

Git has man pages, but basically instead of flags, we have a family of
commands we run as the second argument. When you’re having issues with
git, basically the right move is to check out google and find a useful
resource for the problem you are having. Search the error code and
someone out there will have fixed it before, I promise.

After we check status, edit your hello.html file and change what the
text says in the header and body. Verify in your browser that the change
worked! Now run `git status` again! What changed?

You will be seeing that you have one “untracked” file now, basically
meaning that git knows you made changes but isn’t going to do anything
with them. So first, you have to get that file to be “tracked”.

``` default
$ git add hello.html 
```

To be even faster, you could have run `$git add *`. Now check git status
again.

Verify your changes have been tracked and let’s commit them!

``` default
$ git commit -m "modified hello"
```

That commit -m puts your tracked changes into the local repo, and writes
a message to the log with whatever you specified. If this fails, and it
will if you've never set up git on your local computer before, run the
commands in the error message to set your name and email. Once that has
been done, run the commit again and it should work!

Check `git status` to ensure your commit worked. You should see now that
you are one commit ahead of the remote repo.

If you check that remote repo on Github you will see that nothing has
happened there yet. To get something to happen on Remote, you need to
“push”.

Before pushing, we need to know the name of remote. Most of the time we
can guess it will be origin, but if you are doing fancier things really
anything could be there. To check the name, run `git remote`. 

After verifying the name is origin, run `git push origin main`.

You will get an error message here! Github has decided to no longer
allow password-based authentication for pushing to repositories. You can
read more about this here:
<https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/#what-you-need-to-do-today> 

Using Google and links provided to you, generate a personal access token
and use that to authenticate the next time you push. Make sure to save
that access token somewhere safe, and don't commit it to any of your git
repos!!!! 

Once `git push origin main `has succeeded, check your github repo and
verify the changes have been made. Congratulations on your first ever
push!

### Pull!

Now, let’s get a pull in! Pulling is the act of taking code from
somewhere else and bringing it into a repository. First, let’s make a
change in your Github repository! From the website, update the name in
your README.md to say your name by clicking on the edit button in the
GUI and committing your changes. You can probably guess by now that your
local copy of the repo will not have that change yet, but you can verify
if you want.

So now, your local repo is one commit behind the remote one… time to fix
that!

``` default
$ git pull origin main
```

Git pull combines two commands “fetch” and “merge”, which fetch the
remote repo and merge the two repos together. For more complicated
things, you might have to or want to fetch and merge separately, but
life is easier with a one command pull on a simple repo like this.

Verify the change has been made locally and congrats! You now have more
git knowledge than the average computer science graduate. Practical
skills rock!

All things considered, git and Github are incredibly complicated and
this simple little demo might have oversimplified things, but
honestly... this is good enough to start! You'll be using plenty more
git throughout the rest of the course and believe me, you will find
plenty of ways to break it, and then fix it back up again. (And worst
comes to worst, you can always just make a new repo!)

# Assignment:

1.  Explain what open source is in a few sentences and what the benefits
    are.
2.  Submit a link to your first repo
