# Operating Systems

<iframe allowfullscreen height="360" src="https://www.youtube.com/embed/UoaR2bzFDKE?wmode=opaque" width="640"></iframe>What
is an operating system or OS?

Most likely, just based off of your everyday use you have a pretty good
idea about how to use Windows. However, what we are about to go over is
what is actually occurring under the hood. For the everyday user of a
computer, there is no need to know any of this, but as hacker, with the
need to understand the underlying systems, learning the inner workings
of operating systems is a necessity. In order to master the system you
must remove the blind spots that will limit your ability to grow.

# Abstraction

The technical word for these blind spots is "abstraction". Abstraction
is a word that can be found outside of technical spaces to mean a way of
removing specificity in order to understand more easily. To quote
wikipedia: "Conceptual abstractions may be formed by filtering the
information content of a concept or an observable phenomenon, selecting
only the aspects which are relevant for a particular subjectively valued
purpose. " This whole course I try to abstract away the things you don't
need, so you are left with what matters.

Similarly, Operating Systems abstract away the requirement for end users
to be able to program or know how to set up a network connection, or
really do most things with their computer.

Everything is handled for the average user by the Operating System...
but you are no longer the average user. Over the next few chapters we
will remove more and more abstractions from our view of how computers
work. Each abstraction we remove will show us an entirely new world of
extraordinarily complicated material that was just below the surface. It
might seem overwhelming, but remember, nobody understands all the
abstractions. It is good to know they exist, and that there is something
underneath where you are operating, but there is no need to fully
understand the underlying technology to do great work.

We don't have to care about any of this to be great, which is pretty
amazing.

<a href="https://en.wikipedia.org/wiki/Linux" rel="noopener"
target="_blank"><img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/9d6/486/5b5/1629584983605.jpg"
class="fr-fic fr-dii"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/9d6/486/5b5/1629584983605.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/9d6/486/5b5/1629584983605.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/9d6/486/5b5/1629584983605.jpg?width=1920&amp;dpr=3 3x" /></a>

## Basics

So what really is an operating system? In short, an OS is the interface
between the end user and the computer hardware.

To start, the hardware is generally controlled by something known as
firmware, which is the code built into the electronics that tell them
all how to run as individual components. Firmware is the OS for the
hardware, but on a normal computer, is not considered part of the OS the
user interacts with.

<a href="https://en.wikipedia.org/wiki/Operating_system" rel="noopener"
target="_blank"><img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/344/f30/406/1629584981534.jpg"
class="fr-fic fr-dii"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/344/f30/406/1629584981534.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/344/f30/406/1629584981534.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/344/f30/406/1629584981534.jpg?width=1920&amp;dpr=3 3x" /></a>

Coordinating individual hardware components is the kernel, the core of
the operating system, which coordinates those individual components so
that the computer can run. Software, as we think of it, is the code that
a user interacts with, but the kernel, even if we never interact with it
directly, is still software as the core of the OS. Running on top of the
OS is more software, which are what we think of as processes and
programs. These user processes interface with the OS, which then do all
the work with the kernel to ensure the processes work properly.

## Responsibilities of an Operating System

We know that the OS is responsible for ensuring hardware is used
appropriately, but what does that look like? First we have to think
about what hardware is on a computer. Some important pieces of hardware
are:

-   Central Processing Unit (CPU)
    -   The circuitry which executes the instructions that the OS gives
        it. Don't worry too much about what this means beyond the idea
        that processes are a series of instructions that need somewhere
        to run, and it happens here. We'll get to that eventually
    -   There can be multiple CPUs in a computer, and multiple processes
        on a CPU. There is a ton of complexity here that we are able to
        abstract away. Thanks Operating Systems!
-   Random Access Memory (RAM)
    -   RAM are chips that provide fast, temporary storage for
        information and is required for computers to run quickly. The OS
        uses RAM to ensure that the CPUs get the information they need.
-   Input/Output (I/O) Devices
    -   Hard Drives/Storage Devices
        -   These storage devices are slow, but can contain a great deal
            of information. Data from 'file systems' is loaded into RAM
            by the operating system when needed.
    -   Mice/Keyboards
        -   The OS listens for mouse movements and key presses and
            responds so that a user can drive the OS.
    -   Monitors
        -   The OS displays what is going on so the user can see what is
            happening
        -   The OS doesn't need the monitor to run, but the user needs
            it
        -   ... and many more

Now that we have discussed some of the hardware, we will discuss the
most important roles of an OS.

1.  Processor Management: The OS prioritizes which processes are run by
    the CPUs at what time, ensuring smooth execution.
2.  Memory Management: The OS prioritizes what goes in RAM for the CPUs
    to access. If a CPU needs information and it isn't in RAM yet, the
    computer will run slowly.
3.  Device Management: The OS manages I/O Devices and passes them to
    different processes as required.
4.  File Management: The OS keeps track of files and organizes them, as
    well as passes access to different processes.
5.  Security: If defenses are programmed in, the OS attempts to identify
    unauthorized uses of files and memory and attempts to defends itself
6.  Logging and Error Detecting: The OS saves information as it runs to
    logs to enable troubleshooting of processes
7.  System Performance: In addition to Processor and Memory management,
    the OS keeps track of how processes and the OS as a whole are
    running, and will kill or pause processes as required for smooth
    operation

## Families

There are a few major families of OSs, most notable Unix-Like and
Windows. Both have a long history (and rivalry), but as you can see in
the chart below, the open source UNIX has grown into a vast family of
very different OSs, while Windows has steadily progressed to the modern
Windows 10. You don't need to memorize anything in this, but it's good
to know.

``` default
UNIX-> Unix-Like  
     -> Linux (The Most Popular OS for servers)                      
          -> Ubuntu, Debian, Fedora, Arch, Gentoo (Major Linux OS families)            
          -> Android (Most popular OS in the world)                     
          -> Chrome OS                      
          -> Raspberry Pi                    
            Many many more                  
     -> BSD (Berkeley Software Distribution)                    
          -> MacOS (Partially Linux, mostly closed source)                      
          Many many more

For a visual depiction of the Unix family:
```

<a href="https://en.wikipedia.org/wiki/Unix" rel="noopener"
target="_blank"><img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/a8f/ea2/09c/1629584982269.jpg"
class="fr-fic fr-dii"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/a8f/ea2/09c/1629584982269.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/a8f/ea2/09c/1629584982269.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/a8f/ea2/09c/1629584982269.jpg?width=1920&amp;dpr=3 3x" /></a>

Windows is less interesting, but still worth pointing out the
highlights.

``` default
Windows  
- MS-DOS (1981)  
- Windows 1,2,3,95,98,ME,NT, 2000 (1985-2000)  
- Win. XP (2001)  
- Win. Vista (2006)  
- Win. 7 (2009)  
- Win. 8 (2012)  
- Win. 10 (2015)
```
