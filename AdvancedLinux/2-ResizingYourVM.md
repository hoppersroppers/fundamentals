# Resizing Your VM
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
While we are on the topic of storage and drives, let's spend a little time on one of the more stressful and complicated parts of computing, modifying hard drives. 

I mentioned the ```dd``` command, aka disc destroyer, earlier, but now we are going to do one of the easier and more common tasks you can find yourself having to do. When you built your VM the first time, you probably just agreed to whatever the default virtual hard drive space was and that's how your system was built. 

But now, you're installing all these new packages, downloading all these memes, and you will find yourself running out of space. Running out of space can look very weird on Linux, from not being able to log in, to random bugs in programs, to just getting notifications that you can't make any new files. 

Let's learn how to resolve that by expanding our virtual hard disc! 

# Best Practices

Any time, and I mean, any time you are playing around with hard disc stuff, just make a backup of your filesystem ahead of time. Usually you'd do this with ```dd``` but because we are a VM it is as easy as taking a snapshot. Go play through your virtualization software's settings to take a snapshot. 

Once you have expanded your disk and nothing is broken, then you can delete the snapshot. Look at you, following best practices. 

# Expand Your Virtual Disk

Starting from what we already know, let's think about this in terms of partitions. We know we only have one partition in our virtual disk right now. Let's say it looks like this.

```
__ Virtual Disc: 20 GB_______________
|__Ubuntu Partition __20 GB_______|

```

So all 20 GB of the virtual disc are occupied by our partition, which means our first action is to expand our Virtual Disc size. This will change based off of your Virtualization software, so here are some links. For now, let's just increase your VM disk size by 2 GB.

1. [VMWare Expand](https://docs.vmware.com/en/VMware-Workstation-Player-for-Windows/16.0/com.vmware.player.win.using.doc/GUID-73BEB4E6-A1B9-41F4-BA37-364C4B067AA8.html)
2. [VirtualBox Expand](https://askubuntu.com/questions/88647/how-do-i-increase-the-hard-disk-size-of-the-virtual-machine)
3. [HyperV Expand](https://www.nakivo.com/blog/increase-disk-size-hyper-v-complete-guide/)

It's all pretty straightforward for the virtualization software, but you will notice you have to turn off the VM. Once you're done, your virtual hard drive will look something like this.

```

__ Virtual Disc: 22 GB______________________
|__Ubuntu Partition __20 GB_______| _______|

```

Those extra 2 GB hanging out are called "unallocated space". Sounds badass right?

So even though you resized the disc, your partition is still the same size and you'll still have out of disk space errors. The next step to fix this is to expand the partition out to fill the entire space. 

As a side note, there's a [Maryland hackerspace named Unallocated Space](https://www.unallocatedspace.org/) and they're really cool folks.

# Expanding Your Partition

Now there are hundreds of ways to expand your partition, most of which involve ```gparted``` which would be my recommendation if you were doing something more complicated... but we are not. 

For now, we will use [this sequence of commands](https://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed), which I found in a StackOverflow post. To the best of my knowledge, this is the easiest way to expand your partition out there. 

1. Use ```df -h``` to find the name of your partition. Look for the one that is the largest.
1. enter the command ```cfdisk```.
2. Choose the partition to extend and select "Resize". 

![SO Resize](https://i.stack.imgur.com/RXYeh.png)

3. Set the "New size", filling up the rest of the available area.
4. After pressing enter, you'll see screen with the following note "Partition [someNumber] resized": 

![SO Resized](https://i.stack.imgur.com/IFWXb.png)

5. Next you'll need to "Write" to save your changes. Type "yes".
6. Quit cfdisk. When you exit you may see message "syncing disks", but either way good things are happening.


7. Get filesystem name again for next step with ```df -h```. Nothing should have changed yet.

Now using the name you found for the filesystem, run the following command with ```resize2fs```.  This command will automatically match the size of the partition to the size of the available disc space. Magic!

```
 $ resize2fs /dev/nameOfFilesystem
 resize2fs 1.42.13 (17-May-2015)
 Filesystem at /dev/nameOfFilesystem is mounted on /; on-line resizing required
 old_desc_blocks = 1, new_desc_blocks = 2
 The filesystem on /dev/nameOfFilesystem is now 4854784 (4k) blocks long.
```

8. Then verify everything worked using ```df -h``` again to see the size change.

```
__ Virtual Disc: 22 GB______________________
|__Ubuntu Partition __22 GB_______________|

```

Now you have changed your VM size, which is a huge win for something that is usually very stressful. The next time you have to do this, or help someone else, refer back to this!

# Add More Processing Power to Your VM

While we are here, let's also look at what we can do to speed up your VM. If you haven't tried it already, play around in the options to add another CPU, or add some extra RAM. See what the constraints are. We don't need to worry too much about the effects of adding another vCPU or extra RAM are to our system, but it's worth checking out for the knowledge.

## Assignment:

1. What is a snapshot?  Why are they useful? 
2. Why do you think we have to turn off the VM to resize the virtual hard disk?
3. Why do you think we can expand the partition while the VM is running?
4. Why do you think we don't have to turn off the VM to resize the RAM? 

Answer in the usual format, one or two sentences. This is more about your feelings and what you can find in 5 minutes of research than a perfect answer. Don't research this too deeply or you might lose your mind!




##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->