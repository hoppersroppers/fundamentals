# Install Virtualization Software
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
The major step we need to take is to begin using Linux in our everyday life so that we can get comfortable in the environment we will be working from. If you are already using a Linux box as your home operating system, or already have a VM installed, skip this section: we are only building a VM so that we can learn in it. We will not do anything in this course that will break anything.

If you are on  Windows 10 Enterprise, Pro, or Education, you can use Hyper-V, which is virtualization software built directly into the Windows operating system. Read [this](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v) if you want to know more. Windows 10 Home edition (which you probably have) does not have Hyper-V. All things considered, I really don't like Hyper-V and I do not recommend it, even if you have it available.

If you are on Windows 10 Home or are on an older version of Windows (which you shouldn't be because you update your OS), you have to use a different virtualization tool. I recommend [VMWare Player](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html), as that has been what I have always used, however there are many alternatives, primarily VirtualBox. Both VMWare and VirtualBox are significantly better than Hyper-V, you can't go wrong with either and there is a ton of documentation on both.

If you are on Mac you should use VirtualBox because it is free and generally works well on Macs. [This](https://siytek.com/ubuntu-mac-virtualbox/) is a pretty good link.  

If you are on a locked-down computer that you can't install anything on like a Chromebook, or only have a mobile device, I highly recommend going and heading off to "The Cloud". Many companies offer online VMs for you to use, with a great free trial offering. I recommend using free [Google Cloud](https://cloud.google.com/) for a pretty seamless browser based experience, and an app that works great for mobile access.

**NOTE: No matter what virtualization software you have installed, everything that happens inside the VM will remain the same so it will not hurt your ability to learn from this course.**

This should all be fairly straightforward but will require some Googling, depending on what you are trying to install. If you have any problems that take more than 15 minutes to get through, post in #techsupport with your problem and someone will help you!

As you work through the installation, I want you to practice creating documentation. Using the following format, write a brief walkthrough on how you installed the Virtualization Tool of your choosing. This is not meant to be a comprehensive tutorial on how to do this with images and full explanations, but rather, just enough to get yourself through the process again, and contain any notes on terminology or things you learned so that you can refer back in the future. If you already have a VM or were very confident in your ability to install, I don't expect there to be much in the way of steps or notes.

```
Operating System/Version:
Virtualization Tool:
Primary Resources Used:
1. https://
2. https://

Steps:
1.
2.
3.
...

Notes:
1.
2.
3.
...

```

An example step I would like to read is:
"1. Using Resource 1, follow steps 2-7 to ensure virtualization is enabled in BIOS "

An example note I would like to read is:
"1. BIOS is the firmware used to load an operating system and provides configuration options"

Don't beat yourself up making the walkthrough too detailed, this resource is for you. I want this to be heavy on resources, light on steps, and heavy on notes. Only briefly discuss the trouble shooting process you took to fix things. When you submit the assignment it will be marked as complete.

Hyper-V Notes:

1. There are Virtualization Based Security measures on Windows that when enabled, will not allow you to run VMs other than inside of Hyper-V. If you are running Hyper-V and want to learn more, [watch this](https://www.linkedin.com/learning/microsoft-cybersecurity-stack-advanced-identity-and-endpoint-protection/what-is-virtualization-based-security). You won't understand most of it, but it is interesting and will explain why you will not be able to run a Virtual Machine on top of Hyper-V.
2. Always know what you are disabling or doing before you run random commands off of the internet. In this case, you are disabling a few high level defensive measures that Windows provides for you, notably Credential Guard, Device Guard, and sandbox execution. This isn't terrible, but it does slightly increase your risk.