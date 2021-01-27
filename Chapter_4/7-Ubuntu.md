## History of the Linux Kernel
As mentioned back in Operating Systems, the kernel is the lowest level of the operating system that interacts with the hardware. This means that once the kernel is written, you can build whatever OS you want on top. UNIX, the ancestor of Linux, was written by Ken Thompson and Dennis Ritchie at Bell Labs and was the first modern OS. It was portable, meaning it could run on different hardware (which was a big deal at the time) and quickly became the OS of choice. However, because it was commercially licensed, some hackers, specifically a Finn named Linus Torvalds thought he could do better.

Linus became writing a new kernel, now known as the Linux kernel, as a one-man show. After a few years of development with others this free, open-source, highly portable kernel began to take over the world. Better than anything else out there, Linux quickly rose in popularity and became the dominant Unix-like OS. Since then, Linus has held tightly to his philosophical and technical control of the Linux kernel, but watched the surrounding OSs begin to grow.

## Ubuntu
As the Linux kernel was open-source, it was remixed and edited by plenty of people who had different philosophies. Competing OSs grew around the kernel and now there is a thriving ecosystem of open source Linux OSs. One of the most notable is Ubuntu. Ubuntu is an ancient African word meaning ‘humanity to others’. It is often described as reminding us that ‘I am what I am because of who we all are’.

A group of developers banded together in 2004 and formed a company named Canonical, which is responsible for the Ubuntu operating system. They release Ubuntu for free, in addition to providing consulting services for companies which use Ubuntu servers.

Ubuntu was derived from the Debian family of Unix-like OSs, so under the hood a lot of the OS looks like Debian. The primary difference between between Debian and Ubuntu is that Ubuntu is meant to be easy to set up and use for beginners, while Debian is targeted at a more advanced crowd. As a result of its ease of use, we will be using Ubuntu in this course.

___

## Shells
In computing, a shell is a computer program which exposes an operating system's services to a human user or other program. It is named this because it  is the outer layer ("shell") around the OS, and any attempt to modify the OS goes through it. The way users modify the OS is by accessing either a Graphical User Interface (GUI) shell or a Command Line Interface (CLI) shell.

While the kernel is the base of the OS, the shell is what interfaces with it and is the most visible part of the OS.

## Graphical User Interface

We are most familiar with GUIs as that is what we use to navigate devices in our everyday life. Anytime we find ourselves using a mouse or a touch screen, or really find ourselves doing anything other than typing, we are using a GUI.

Something that is interesting to note about many Linux OSs is that some images ship without a GUI, especially images labeled for "servers". This means the OSs on these images can only be controlled from the command line. Early versions of Windows had the ability to run like this, but now all versions of Windows come with a GUI, even if it is not needed.

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

We won't be doing much work with Windows in this course, so we will focus on learning the Bash Shell. For your first trick, the shell by typing ctrl-alt-t, all at the same time.

 * Check to see your network settings by running the bash command "ifconfig"
 * Just doing that and leaving the terminal open in the corner makes you look like you know what you are doing, even if you learn nothing else from this course
 * You're welcome.

 For your next trick, we are going to modify your wallpaper entirely from the command line.

 First we have to download an image, and then we will use the command to make it our background.

 ```
$ wget -O /tmp/wallpaper.jpg "https://github.com/hoppersroppers/hoppersroppers.github.io/raw/master/_layouts/constitution.jpg"
$ gsettings set org.gnome.desktop.background picture-uri file:////tmp/wallpaper.jpg
```

Now your background image should be a picture of a ship! If it didn't work, troubleshoot.

## Assignment

```markdown
Questions:

1. Using the 'man' command, describe what the command using wget and the -O flag did
2. Using the 'man' command, describe what the comand using gsettings did

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

___
Just like on any operating system, one of the first things you should do after installing Ubuntu is to make sure all the software is updated. This minimizes the number of bugs we encounter, as well as helps to patch our computer against vulnerabilities. Make sure to update your Host OS as well, and that you install patches to your Virtualization Tool. Having all of these updated ensures a smooth and secure experience.

# Sudo and Privilege

Before we get into updating things, first we need to talk about privilege. No, not that kind, though it's worth talking about. In this course we will be discussing Linux privileges.

By default, Linux only allows certain users the ability to access some files. You will learn more about why and how this is implemented, but for now, just know that the standard user, you, is not allowed to update files controlled by the OS or other users. This is generally so that you don't break anything by accident, but also as a security feature to prevent a malicious user or process from stealing information or breaking things.

The command 'sudo', which stands for "superuser do", is used to escalate privileges up to the level of the account used for system administrator. Oftentimes on Linux systems, this is referred to as "root". A user or process with root access has the ability to read, write, and modify anything on the system. As a best practice, instead of always using root, we log in as a normal user, and only use root privileges when we need to. This is referred to as the Principle of Least Privilege, and if you are interested you can learn more about it in our [Security course](https://academy.hoppersroppers.org/mod/assign/view.php?id=894).

To run a command with root privileges, all we have to do is put the command 'sudo' in front of the command we want to run. When we do this we will be prompted for the root password, and if we enter it correctly the password will be checked against the correct files and the desired command will be executed with root privs.

That was a long winded response, and believe me, I skipped over some detail, but this is what you need to know for now. You'll learn more in the Permissions section.

## Packages

Packages are what Linux OSs use to distribute and maintain software. They are custom file formats that usually contain an archive of compressed files that are used to install, as well as some metadata that describes how to install and what the dependencies are. Dependencies are a list of what other programs a piece of software need to be installed in order for it to run. Developers use packages to build programs that are easy to install and run across many different machines. As long as the package installs itself properly, the program will work!

For example, if you are installing an image editing program named Program 1, it might have a single dependency which is named Program 2 that is used to open image files. When Program 1 attempts to install itself from a package, it will check its dependencies and find Program 2, and if Program 2 is not available, it will stop the installation. After you install Program 2, and then rerun the command to install Program 1 and it will succeed.

On Ubuntu, the package management system is named DPKG, or Debian Package, as Ubuntu is based on the Debian OS. 'apt' and 'apt-get' are front ends for the DPKG system, and allow command line access to update and install new packages. Ubuntu also has the ability to download .deb files and install them using system tools, either from the command line or the GUI.

In addition to the default package management system, there are 3rd party managers for different pieces of software like Python, as well as different file formats that developers can choose to release their software with instead of DPKG.

Finally, you can compile programs from source using the correct compilation arguments. This is the old school way to do it, but it is much more difficult and is rarely recommended by the developers who release software.


## Update Packages

We will use apt-get because it has slightly more features. When dealing with packages, 99% of the time we will only need three commands.

```
$ sudo apt-get update
```
As a first note, any time you are working with packages you will want to use sudo in order to ensure you have the permissions to install new packages.

This command will use apt-get to update the list of available locations and dependencies for all the repositories and Personal Package Archives (PPAs) that are saved on the computer. This does not update any software, rather it updates the saved locations and version numbers of all the software that is saved on our computer. There's a little more complexity than this, but don't worry about it for now.

Run the command now to update.

```
$ sudo apt-get upgrade
```
This command will check the list of packages that you just updated with ```apt-get update``` and then download and  upgrade any packages on your computer that need upgrading. If you don't run update first, you won't upgrade anything.

By running update and then upgrade you will ensure everything on your system is fully up to date, but be warned, it can take a while.

```
$ sudo apt-get install foobar
```
This command will install the most recently updated version of the program "foobar". Again, always ensure to run update first or you might get an old version.

## Install Some applications

1. Install Gnome Tweak Tool from the command line and do something interesting
   * ```sudo apt-get install gnome-tweaks```
      * Don't worry too much about what this command does, soon you will understand
   * As an interesting note, Gnome is the default GUI that comes with the Ubuntu OS, but that was not always the case. If you really wanted to, you could replace the Gnome GUI with a different GUI due to the open source nature of Linux OSs.
2. Install Google Chrome (or another browser) using a .deb file
  * .deb is the file extension for a Debian package, as Ubuntu operates under the Debian system. Any .deb file should work on Ubuntu.
  * If you're looking for a more lightweight browser try Chromium, and if you're into privacy, check out Brave. Both have .deb files

3. Install the art program GIMP via the 3rd party package manager FlatPak and make a meme!
  * Post your meme in the Slack in the channel #course_computing.

As you can see, there is some surprising complexity in how we install files on Linux... but let's not worry about that too much yet. Hopefully this section gave you some confidence doing uncomfortable activities.

# Assignment
Submit a screenshot showing your newly installed browser.
