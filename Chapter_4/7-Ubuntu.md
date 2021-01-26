# Ubuntu
Use the fantastic site LinuxJourney to learn about Linux history.

Then read, from the same section, Lessons 2 and 5. <https://linuxjourney.com/lesson/linux-history>

As mentioned in the Operating Systems section, from Unix came Linux, and from Linux came Ubuntu, the most common of all Linux operating systems. Read about Ubuntu here. <https://ubuntu.com/about>

## Shells
In computing, a shell is a computer program which exposes an operating system's services to a human user or other program. It is named this because it  is the outer layer ("shell") around the OS, and any attempt to modify the OS goes through it. The way users modify the OS is by accessing either a Graphical User Interface (GUI) shell or a Command Line Interface (CLI) shell.

## Graphical User Interface

We are most familiar with GUIs as that is what we use to navigate devices in our everyday life. Anytime we find ourselves using a mouse or a touch screen, or really find ourselves doing anything other than typing, we are using a GUI.

Something that is interesting to note about many Linux OSs is that some images ship without a GUI, especially images labled for "servers". This means the OSs on the images can only be controlled from the command line. Early versions of Windows had the ability to run like this, but now all versions of Windows come with a GUI, though it is not needed.

## Command Line Interface

The command line interface, or CLI, is a text based interface used to interact with the OS. When you think about hackers typing text into a black screen and running commands, they are operating with the CLI. Not only does it look really cool, it is also a very efficient way to run programs. For example, typing a few characters into the CLI can accomplish what 20 mouse clicks could do while operating through the GUI.

Both Linux and Windows have CLIs that we will be operating with as power users.

Linux:
* There are a variety of shells that exist in the Linux ecosystem, but the default is Bash (Bourne Again SHell) that we discussed in your Second Assignment. Bash

Windows:
* CMD
  * A legacy interface that allows access to DOS commands
    * MS-DOS was the first Microsoft OS and contained many basic features that are still accessible via CMD
* Powershell
  * A fully featured interface and language that allows complex scripting via cmdlets and pipes. As the entire language was written for working with Windows, it allows fine grained control and easy manipulation of the OS.
* Windows Subsystem for Linux (WSL) - Windows 10 Only
  * The Windows Subsystem for Linux lets developers run a Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.
  * Basically, it's a mini-Linux VM, with access to all the same files on the host Windows machine.

## Personalize

Now that the VM is yours, it is time to personalize it. Going forward, I strongly recommend that you do everything in your Linux VM. That means your homework, checking your emails, listening to music, anything. The more time spent immersed the better off you will be.

Recommended Tasks:

0. Open the terminal by typing ctrl-alt-t at the same time.
   * Check to see your network settings by running the bash command "ifconfig"
   * Just doing that and leaving the results in the corner makes you look like you know what you are doing, even if you learn nothing else from this coursess
1. Change the wallpaper to something cool

Next I am going to have you install programs from a variety of sources. There is nothing in here that is for power users yet, this is just to help you make your VM habitable. As an aside, don't worry about typing in your password to install things on Linux. This is normal behavior anytime you use higher level permissions. If you have any problems, ask in #techsupport.

2. Install Google Chrome using a .deb file
  * If you're looking for something more lightweight try Chromium, and if you're into privacy, check out Brave
3. Install Gnome Tweak Tool from the command line and do something interesting
   * ```sudo apt install gnome-tweaks```
      * Don't worry too much about what this command does, soon you will understand
   * As an interesting note, Gnome is the default GUI that comes with the Ubuntu OS, but that was not always the case. If you really wanted to, you could replace the Gnome GUI with a different GUI due to the open source nature of Linux OSs.
4. Install the art program GIMP via FlatPak and make a meme!
  * Post your meme in the Slack in the channel #course_computing.

As you can see, there is some surprising complexity in how we install files on Linux... but lets not worry about that too much yet.
