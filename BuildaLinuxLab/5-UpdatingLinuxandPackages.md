# Updating Linux and Packages

<iframe allowfullscreen class="fr-draggable" height="360" src="https://www.youtube.com/embed/iPwi-aTnlls?wmode=opaque" width="640"></iframe>

  

Just like on any operating system, one of the first things you should do
after installing Ubuntu is to make sure all the software is updated.
This minimizes the number of bugs we encounter, as well as helps to
patch our computer against vulnerabilities. Make sure to update your
Host OS as well, and that you install patches to your Virtualization
Tool. Having all of these updated ensures a smooth and secure
experience.

# Sudo and Privilege

Before we get into updating things, first we need to talk about
privilege. No, not that kind, though it's worth talking about. In this
course we will be discussing Linux privileges.

By default, Linux only allows certain users the ability to access some
files. You will learn more about why and how this is implemented, but
for now, just know that the standard user, you, is not allowed to update
files controlled by the OS or other users. This is generally so that you
don't break anything by accident, but also as a security feature to
prevent a malicious user or process from stealing information or
breaking things.

The command 'sudo', which stands for "substitute user do", is used to
escalate privileges up to the level of the username specified in the
command. 'sudo' defaults to administrator access, which on Linux systems
is referred to as "root", if no username is specified. (For a fun fact,
'sudo' used to stand for "superuser do", but it has over time shifted to
substitute user.) A user or process with root access has the ability to
read, write, and modify anything on the system. As a best practice,
instead of always using root for our everyday activities we log in as a
normal user, and only use root privileges when we need to, using 'sudo'.
This is referred to as the Principle of Least Privilege, and if you are
interested you can learn more about it in our [Security
course](https://academy.hoppersroppers.org/mod/assign/view.php?id=894).

To run a command with root privileges, all we have to do is put the
command 'sudo' in front of the command we want to run. When we do this
we will be prompted for the root password, and if we enter it correctly
the password will be checked against the correct files and the desired
command will be executed with root privs.

That was a long winded response, and believe me, I skipped over some
detail, but this is what you need to know for now. You'll learn more in
the Permissions section.

<a href="https://xkcd.com/149/" rel="noopener" target="_blank"><img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/48c/227/707/1629593263354.jpg"
class="fr-fic fr-dii"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/48c/227/707/1629593263354.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/48c/227/707/1629593263354.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/48c/227/707/1629593263354.jpg?width=1920&amp;dpr=3 3x" /></a>

## Packages

Packages are what Linux OSs (basically all OS, programming languages,
etc) use to distribute and maintain software. They are custom file
formats that usually contain an archive of compressed files that are
used to install, as well as some metadata that describes how to install
and what the dependencies are. Dependencies are a list of what other
programs a piece of software need to be installed in order for it to
run. Developers use packages to build programs that are easy to install
and run across many different machines. As long as the package installs
itself properly, the program will work! Without package managers,
installing things would be very painful, and nobody would use new
software. With them... still painful, but at least better.

For example, if you are installing an image editing program named
Program 1, it might have a single dependency which is named Program 2
that is used to open image files. When Program 1 attempts to install
itself from a package, it will check its dependencies and find Program
2, and if Program 2 is not available, it will stop the installation.
After you install Program 2, and then rerun the command to install
Program 1 and it will succeed.

On Ubuntu, the package management system is named DPKG, or Debian
Package, as Ubuntu is based on the Debian OS. 'apt' and 'apt-get' are
front ends for the DPKG system, and allow command line access to update
and install new packages. Ubuntu also has the ability to download .deb
files and install them using system tools, either from the command line
or the GUI. While there are minor differences between 'apt' and
'apt-get', they do basically the same thing and I am more used to using
'apt-get' and you'll see many more examples of it on the internet so
that is what I teach.

In addition to the default package management system, there are 3rd
party managers for different pieces of software like Python, as well as
different file formats that developers can choose to release their
software with instead of DPKG. Honestly, it is a bit of a nightmare
keeping them all straight, but at least you can usually google the name
of the program and the package manager to get troubleshooting
directions.

Finally, you can compile programs from source using the correct
compilation arguments. This is the old school way to do it, but it is
much more difficult and is rarely recommended by the developers who
release software.

## Update Packages

We will use apt-get because it has slightly more features (and it's what
I'm used to). When dealing with packages, 99% of the time we will only
need three commands.

``` default
$ sudo apt-get update
```

As a first note, any time you are working with packages you will want to
use sudo in order to ensure you have the permissions to install new
packages.

This command will use apt-get to update the list of available locations
and dependencies for all the repositories and Personal Package Archives
(PPAs) that are saved on the computer. This does not update any
software, rather it updates the saved locations and version numbers of
all the software that is saved on our computer. There's a little more
complexity than this, but don't worry about it for now.

Run the command now to update.

``` default
$ sudo apt-get upgrade
```

This command will check the list of packages that you just updated with
`apt-get update` and then download and upgrade any packages on your
computer that need upgrading. If you don't run update first, you won't
upgrade anything.

By running update and then upgrade you will ensure everything on your
system is fully up to date, but be warned, it can take a while.

This is the format for installing a new program. "Foobar" is a
programming joke that just means a placeholder word. If you see
"foobar", "foo", or "bar" anywhere, it almost always means it's a
placeholder for something else.

``` default
$ sudo apt-get install foobar
```

This command would install the most recently updated version of the
program "foobar", if the program "foobar" existed. Again, always ensure
to run update first or you might get an old version.

In the next section we will actually use it for real.

Continue when all your updates are complete.
