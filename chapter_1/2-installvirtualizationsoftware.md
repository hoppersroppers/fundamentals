# Install Virtualization Software

[Check out our free course!](https://academy.hoppersroppers.org/mod/page/view.php?id=669)

Install free virtualization software to run your virtual machine in! 

If you are on Windows 10, just use Hyper-V, which is virtualization software built directly into the Operating System. Read this for more information: <https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v>

If you are not on Windows 10 (you should be), I recommend VMWare Player, as that has been what I have always used, however there are many alternatives, primarily VirtualBox. One good thing about VirtualBox is that it is free on Macs. 


If you are on a locked-down computer that you can't install anything on like a school Chromebook, I highly recommend going and heading off to "The Cloud". Many companies offer online VMs for you to use, with a great free trial offering. I recommend using Google Cloud for a pretty seamless browser based experience.  <https://cloud.google.com/>

**NOTE: No matter what virtualization software you have installed, everything that happens inside the VM will remain the same so it will not hurt your ability to learn.**

[https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html)

This should be fairly straightforward but will require some Googling. When you are complete, submit a screenshot of your Virtualization Software. If you are on Windows, use the Microsoft 'Snip' tool to forever change your screenshot game. Just type "Snip" into the search bar and it will appear.

Notes:

1. There are Virtualization Based Security measures on Windows that when enabled, will not allow you to run VMs other than inside of Hyper-V. Watch this video to learn more <https://www.linkedin.com/learning/microsoft-cybersecurity-stack-advanced-identity-and-endpoint-protection/what-is-virtualization-based-security>. You won't understand a lot of it, but it is interesting and will explain why you will not be able to run a Virtual Machine on top of it. 
2. Always know what you are disabling or doing before you run random commands off of the internet. In this case, you are disabling a few high level defensive measures that Windows provides for you, notably Credential Guard, Device Guard, and sandbox execution. This isn't terrible, but you should try to remember to turn Hyper-V back on when you are done using your VM because it makes you safer.

[Visit the course page!](https://academy.hoppersroppers.org/mod/assign/view.php?id=669)
 