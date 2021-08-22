# Install Virtualization Tools
Virtualization tools are pieces of software that connect your host OS with your new VM. You need this for a lot of critical usability things, and usually it doesn't come pre-installed. These virtualization tools are responsible for passing files and clipboard material back and forth, adjusting monitors, and overall ensuring the Host-VM experience is stable.

I'll be honest, getting this working can be kind of difficult sometimes, but you have to figure your own way through this. Again, if you have any trouble, and this takes more than a half hour to figure out, message us in #techsupport and we will help you out. There is no shame, I've had VMs before that I gave up trying to install VMWare tools and just sucked it up for a week. You'll be on this VM for a while, so you need to get it installed.

Before you waste any time trying to install things, you might have already done it during your VM installation. The easiest way to test if VMWare Tools or VirtualBox Guest Addons is installed is to try to copy and paste a file from your host OS to the VM. If it works, you're good!

If you are using Hyper-V, it should be done.

If you are using VMWare, you need to install VMWare Tools for Ubuntu. <https://linuxize.com/post/how-to-install-vmware-tools-in-ubuntu-18-04/>

If you are using VirtualBox, follow this guide to install the VBox Guest Addons. <https://www.tecmint.com/install-virtualbox-guest-additions-in-ubuntu/>

Again, check to make sure it worked by moving files between the Host and the VM. My personal recommendation is to open the file browser in your VM and drag and drop into there. For some reason the Ubuntu Desktop doesn't work nearly as well.

If you have any trouble, reach out in #techsupport for assistance.

When complete, submit a screenshot that shows a file you copied from Host to VM. Don't worry too much about what the file is, this is for progress tracking.
