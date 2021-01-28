# Linux  Filesystem

Here there be dragons! Anytime you start playing with the filesystem, especially the ```dd``` or "disc destroyer" command, you are playing with fire. Do not allow bad things to happen to yourself, always always always triple check what drive you are reading from and writing to. Do not be a victim... I've done it multiple times if we are being honest, but... not recommended.


The Linux filesystem is in a standard hierarchical setup. There are a few different file systems, but the majority use a filesystem named ext4 these days.

We will run this command to see all the filesystems hooked up to our computer!
```
$ df
```
df has a ton of output, but we can ignore most of them, we are looking for your primary drive, so it is almost certainly the largest. Most likely it will be called /dev/sda_ , but who knows! For the rest of this page I will be calling it /dev/DRIVENAME.

Filesystems are split up into blocks for ease of navigation.
```
$ sudo blockdev --getbsz /dev/DRIVENAME
```

The blocksize will probably be 4096, the ext4 default, but it's worth checking.


# Drive Layout

Here is a quick diagram on how the filesystem is laid out on your drive.
```
[B][S][Inode List][ Data Blocks ]
 |  |
 |  +-- Super Block
 +----- Boot Area
```
Don't worry too much about what is going on in the Boot Area or the Super Block yet, that stuff is handled for us by the OS. There's a ton of commands and cool things you can do with that, but I don't want to get into it this early in the game. ```dd``` is the only "footgun" I feel comfortable teaching right now and I want you to respect the filesystem, not play around with it (like we are about to do!!!!!!!!) Before we get into that, let's learn a little bit more about the Inode List.

Inodes are the pointers OSs use to give the location of a block of data. Whether it is for a file or a directory, there will be an inode associated with it. These inodes are all stored together in a table towards the front of a file system on a drive. By reading the data located in the inode table, the OS is able to calculate the correct offset into the Data Blocks required to find the file. This is why inode stands for Index Node, because it helps us find where we put all of our files.

As we said, each file has its own inode number. We can get it with ```ls -i fileName```.

This command will print the inode number for the file. We then copy that number to the clipboard. ```debugfs``` is a powerful tool for working directly with the drive, and we can use this particular incantation to print out the information of the inode we have selected. Anytime you work with ```debugfs``` you should probably have a cheatsheet available. s

```
$ sudo debugfs -R "stat <1521431>" /dev/DRIVENAME
```

There is a lot shown in the output, but the only things that matter to us right now are is the block number, labeled as "Blocks:" or "Extents:"" with a numeric value, for example, "547473". If the file is large enough you might get multiple Extents or Blocks, in which case things get more complicated.

Whether it says Blocks or Events, save that number. It is the number of blocks from the start of the drive that the file is located at.

With that offset number and the block size we can then use the notorious ```dd``` to calculate how far into the drive we need to go find our file. Before running this command, check over what you have as your input and output. Right now the input file is the dummy text "/dev/DRIVENAME" and the output file is "fileRecovered". If you switch your input file and output file once you put the actual drive name in, you will nuke your primary drive. Please do not do that.

~~~
$ dd if=/dev/DRIVENAME of=fileRecovered bs=4096 count=1 skip=547473
~~~

Going through this command in order:

* ```dd``` is the disc mount command
* We specify as the input /dev/DRIVENAME, the drive the file is located on
* We specify as the output fileRecovered, as the file name for whatever we find there
* bs is block size and is set to whatever --getbsz told us for the drive
* count is for the number of blocks we are expecting to find
* skip tells us to skip that number of blocks into the drive to where the inode table told us our file would be

When this command is run, we expect to print whatever is at that location in the drive to be saved into fileRecovered. In this case, it should be the contents of the file we initially got our inode value for.

# What Happens When You Delete a File
When you ```rm``` a file the inode data that tells us what the LBA leading to the file is will be zero'd out. This means that it no longer is useful to find the block offset. Once this inode table has been zero'd out, whatever block it previously reserved is fair game for the file system to put new data in... but that does not mean that the data itself is gone!

If you already know the offset this is easy, use the same command as before with ```dd```. Because it doesn't go through the inode table there is no effect. However, if you don't have the offset not all hope is lost.

# How to Recover a File

***AUTHOR's NOTE: Yes there are sketchy ways to recover a file via processes, but that is like, a lot. Maybe I'll teach it later, but not now.***

First, you want to turn off the computer. Again, once those blocks are freed any process can write in them, and it gets more likely as time goes on. By turning the computer off you guarantee those files can't be written over.

By booting into a turned off computer with a separate OS (this is outside the scope of the course) we can then mount the affected hard drive as read only. From there, we can search through the hard drive for the raw file and hope we can still find it.

Now we are using grep again, this time to look for a known pattern in the file and then take 500 bytes before and after and save it to a file named /tmp/recover, as well as displaying it on the screen.

~~~
$ grep -a -C 500 'known pattern' /dev/sda | tee /tmp/recover
~~~

Instead of using grep we can use an actual recovery tool. Just like grep for a known pattern, file recovery tools know what the file format is for files like images or videos. Instead of needing to know the offset on the drive, they can just scan through until they find the correct file format headers and save the rest of the file. You'll learn more about this in the CTF course.


# Assignment

```markdown
Questions:

1. Where are drives located on Linux?
2. Explain how the inode table is used to find saved files in a few sentences.
3. What happens when you delete a file in a few sentences.

Resources:

0. Google
```
Respond in the usual format.

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
