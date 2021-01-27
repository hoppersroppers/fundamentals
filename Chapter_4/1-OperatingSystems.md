What is an operating system or OS?

Most likely, just based off of your everyday use you have a pretty good idea about how to use Windows. However, what we are about to go over is what is actually occurring under the hood. For the everyday user of a computer, there is no need to know any of this, but as hacker, with the need to understand the underlying systems, learning the inner workings of operating systems is a necessity. In order to master the system you must remove the blind spots that will limit your ability to grow.

The technical word for these blind spots is "abstraction". Operating Systems abstract away the requirement for end users to be able to program or know how to set up a network connection, or really do anything with their computer. Everything is handled for the average user by the Operating System... but you are no longer the average user.

There is a later course on this site specifically for Operating systems, but for now, this section will give you enough to be dangerous, which is all we can ask for.

## Basics
In short, an OS is the interface between the end user and the computer hardware. The hardware is generally controlled by something known as firmware, which is the code that tells the individual components how to work together to run. Software, as we think of it, is the code that a user interacts with. This means that the OS is considered software. Running on top of the OS is more software, which is what we think of as processes. These user processes interface with the OS, which then does all the work with hardware to ensure the processes work properly. The kernel is a special part of the operating system and operates on the lowest level above the hardware. The kernel's specific job is to interface between the hardware and the operating system, writing the instructions that tell the hardware what to do.

## Responsibilities of an Operating System
We know that the OS is responsible for ensuring hardware is used appropriately, but what does that look like? First we have to think about what hardware is on a computer. Some important pieces of hardware are:

* Central Processing Unit (CPU)
  * The circuitry which executes the instructions that the OS gives it. Don't worry too much about what this means beyond the idea that processes are a series of instructions that need somewhere to run, and it happens here. We'll get to that eventually
  * There can be multiple CPUs in a computer, and multiple processes on a CPU. There is a ton of complexity here that we are able to abstract away. Thanks Operating Systems!
* Random Access Memory (RAM)
  * RAM are chips that provide fast, temporary storage for information and is required for computers to run quickly. The OS uses RAM to ensure that the CPUs get the information they need.
* Input/Output (I/O) Devices
  * Hard Drives/Storage Devices
    * These storage devices are slow, but can contain a great deal of information. Data from 'file systems' is loaded into RAM by the operating system when needed.
  * Mice/Keyboards
    * The OS listens for mouse movements and key presses and responds so that a user can drive the OS.
  * Monitors
    * The OS displays what is going on so the user can see what is happening
    * The OS doesn't need the monitor to run, but the user needs it
  * ... and many more

Now that we have discussed some of the hardware, we will discuss the most important roles of an OS.

1. Processor Management: The OS prioritizes which processes are run by the CPUs at what time, ensuring smooth execution.
2. Memory Management: The OS prioritizes what goes in RAM for the CPUs to access. If a CPU needs information and it isn't in RAM yet, the computer will run slowly.
3. Device Management: The OS manages I/O Devices and passes them to different processes as required.
4. File Management: The OS keeps track of files and organizes them, as well as passes access to different processes.
5. Security: If defenses are programmed in, the OS attempts to identify unauthorized uses of files and memory and attempts to defends itself
6. Logging and Error Detecting: The OS saves information as it runs to logs to enable troubleshooting of processes
7. System Performance: In addition to Processor and Memory management, the OS keeps track of how processes and the OS as a whole are running, and will kill or pause processes as required for smooth operation


## Families
There are a few major families of OSs, most notable Unix-Like and Windows. Both have a long history (and rivalry), but as you can see in the chart below, the open source UNIX has grown into a vast family of very different OSs, while Windows has steadily progressed to the modern Windows 10. You don't need to memorize anything in this, but it's good to know.

```
UNIX-> Unix-Like  -> Linux (The Most Popular OS for servers)
                      -> Ubuntu, Debian, Fedora, Arch, Gentoo (Major Linux OS families)
                      -> Android (Most popular OS in the world)
                      -> Chrome OS
                      -> Raspberry Pi
                      Many many more
                  -> BSD (Berkeley Software Distribution)
                      -> MacOS (Partially Linux, mostly closed source)
                      Many many more

Windows
  - MS-DOS (1981)
  - Windows 1,2,3,95,98,ME,NT, 2000 (1985-2000)
  - Win. XP (2001)
  - Win. Vista (2006)
  - Win. 7 (2009)
  - Win. 8 (2012)
  - Win. 10 (2015)
```

## Assignment

```markdown
Questions:

1. What is an operating system?
2. Describe what an operating system is responsible for. (This is a trick question, it's everything.)
3. What is the world's popular operating system? What are the top desktop operating systems?
4. What is the kernel?

Resources:

0. Google
```

Write up a few sentences for each of the questions. All of the answers are on this page, but ensure you answer any Pre-Questions you come up with.


```
 Answers:

 1.
 2.
 3.

 Resources:


 Pre-Questions:


 Post-Questions:


 Feedback:

```
