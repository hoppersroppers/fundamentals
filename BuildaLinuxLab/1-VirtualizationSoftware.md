# Virtualization Software

<iframe allowfullscreen class="fr-draggable" height="360" src="https://www.youtube.com/embed/4UvXPgQv-1w?wmode=opaque" width="640"></iframe>

  

The major step we need to take is to begin using Linux in our everyday
life so that we can get comfortable in the environment we will be
working from. If you are already using a Linux box as your home
operating system, or already have a VM installed, skip this section: we
are only building a VM so that we can learn in it. We will not do
anything in this course that will break anything.

## Windows: 

There is something called Windows Subsystem for Linux or WSL for short,
which allows you to run a Linux OS command-line only directly on your
Windows machine. I don't totally recommend this, but it is very easy to
set up and you should do it now anyway.
<https://learn.microsoft.com/en-us/training/modules/get-started-with-windows-subsystem-for-linux/2-enable-and-install> 

I still recommend you install actual virtualization software so that you
can use Linux tools which require the use of a Graphical User Interface
(GUI).

If you are on Windows 10 Enterprise, Pro, or Education, you can use
Hyper-V, which is virtualization software built directly into the
Windows operating system. Read <a
href="https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v"
rel="noopener" target="_blank">this</a> if you want to know more.
Windows 10 Home edition (which you probably have) does not have
Hyper-V. 

If you are on Windows 10 Home or are on an older version of Windows
(which you shouldn't be because you update your OS), you have to use a
different virtualization tool. I recommend <a
href="https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html"
rel="noopener" target="_blank">VMWare Player</a>, as that has been what
I have always used, however there are many alternatives, primarily
VirtualBox. Both VMWare and VirtualBox are significantly better than
Hyper-V, you can't go wrong with either and there is a ton of
documentation on both.

## Macs

If you are on an older Mac you should use VirtualBox because it is free
and generally works well on Macs.
<a href="https://siytek.com/ubuntu-mac-virtualbox/" rel="noopener"
target="_blank">This</a> is a pretty good link. Due to some very
complicated computer engineering reasons, Macs running on the M1
processor don't work properly with VirtualBox (at this point in time).
If you are using an M1 (jealous!!!) use the free version of VMWare
Fusion. 

## Chromebook/Other

If you are on a locked-down computer that you can't install anything on
like a Chromebook, or only have a mobile device, I highly recommend
going and heading off to "The Cloud". Many companies offer online VMs
for you to use, with a great free trial offering. I recommend using free
<a href="https://cloud.google.com/" rel="noopener"
target="_blank">Google Cloud</a> for a pretty seamless browser based
experience, and an app that works great for mobile access.

If you don't can't do any of those things,
<https://www.hoppersroppers.org/shell/> will work to learn many things,
but it only goes so far. 

**NOTE: No matter what virtualization software you have installed,
everything that happens inside the VM will remain the same so it will
not hurt your ability to learn from this course.**

This should all be fairly straightforward because there are so many
resources but will require some Googling, depending on what you are
trying to install. If you have any problems that take more than 15
minutes to get through, post in \#techsupport with your problem and
someone will help you!

As you work through the installation, I want you to practice creating
documentation. Using the following format, write a brief walkthrough on
how you installed the Virtualization Tool of your choosing. This is not
meant to be a comprehensive tutorial on how to do this with images and
full explanations, but rather, just enough to get yourself through the
process again, and contain any notes on terminology or things you
learned so that you can refer back in the future. If you already have a
VM or were very confident in your ability to install, I don't expect
there to be much in the way of steps or notes.

``` default
Operating System/Version: 
Virtualization Tool: 
Primary Resources Used: 
1. https:// 
2. https:// 
Steps: 
1. 
2.
3. ... 
Notes: 
1. 
2. 
3. ... 
```

An example step I would like to read is: "1. Using Resource 1, follow
steps 2-7 to ensure virtualization is enabled in BIOS "

An example note I would like to read is: "1. BIOS is the firmware used
to load an operating system and provides configuration options"

Don't beat yourself up making the walkthrough too detailed, this
resource is for you. I want this to be heavy on resources, light on
steps, and heavy on notes. Only briefly discuss the trouble-shooting
process you took to fix things. When you submit the assignment it will
be marked as complete.

Hyper-V Notes:

1.  There are Virtualization Based Security measures on Windows that
    when enabled, will not allow you to run VMs other than inside of
    Hyper-V. If you are running Hyper-V and want to learn more, <a
    href="https://www.linkedin.com/learning/microsoft-cybersecurity-stack-advanced-identity-and-endpoint-protection/what-is-virtualization-based-security"
    rel="noopener" target="_blank">watch this</a>. You won't understand
    most of it, but it is interesting and will explain why you will not
    be able to run a Virtual Machine on top of Hyper-V.
2.  Always know what you are disabling or doing before you run random
    commands off of the internet. In this case, you are disabling a few
    high level defensive measures that Windows provides for you, notably
    Credential Guard, Device Guard, and sandbox execution. This isn't
    terrible, but it does slightly increase your risk.

Other Notes:

1.  Virtualization is ludicrously complicated and can simply be
    impossible on specific hardware. Hit up the support channel if you
    find yourself stuck. 
