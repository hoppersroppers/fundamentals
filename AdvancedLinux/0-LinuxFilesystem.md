# Linux Filesystem
##  [Register for the Free Course Today!](https://www.roppers.org/courses/fundamentals)
# Linux  Filesystem

Here there be dragons! Anytime you start playing with the filesystem, especially the ```dd``` aka "disc destroyer" command, you are playing with fire. Do not allow bad things to happen to yourself, always always always triple check what drive you are reading from and writing to. Do not be a victim... I've done it multiple times if we are being honest, but... not recommended. 

# Filesystems 

The Linux filesystem is in a standard hierarchical setup. There are a few different file systems, but the majority use a filesystem named ext4 these days. Don't worry too much about what that means, you can ignore this abstraction 95% of the time. 

There can be multiple filesystems (often called drives) on a single OS. 

We will run this command to see all the filesystems hooked up to our computer!
```
$ df
```
df has a ton of output, but we can ignore most of them, we are looking for your primary drive, so it is almost certainly the largest. Most likely it will be called /dev/sda_ , but who knows! For the rest of this page I will be calling it /dev/DRIVENAME.

'df' does a lot of things ([like expanding hard drives when you run out of space in your VM](https://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed)!), but we won't worry about that right now. 

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
Don't worry too much about what is going on in the Boot Area or the Super Block yet, that stuff is handled for us by the OS and doesn't affect day to day life for us.

Starting with the Inode list, think of it as the front desk of a library that keeps information on all the books (files) in the shelves. You can learn where each book(file) is stored, last time it was checked out, and more from the information in the Inode list. Once you know where the book(file) is, you can use the information you got from the inode list to go look for it. This is what the OS does every time you open a file, but it has been abstracted away from us having to do it. 

Inodes are the pointers OSs use to give the location of a block of data. Whether it is for a file or a directory, there will be an inode associated with it. These inodes are all stored together in a table towards the front of a file system on a drive. By reading the data located in the inode table, the OS is able to calculate the correct offset into the Data Blocks required to find the file. This is why inode stands for Index Node, because it helps us find where we put all of our files.

[<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/File_table_and_inode_table.svg/640px-File_table_and_inode_table.svg.png">](https://en.wikipedia.org/wiki/File_descriptor)


As we said, each file has its own inode number. We can get it with ```ls -i fileName```.

This command will print the inode number for the file. We then copy that number to the clipboard. ```debugfs``` is a powerful tool for working directly with the drive, and we can use this particular incantation to print out the information of the inode we have selected. Anytime you work with ```debugfs``` you should probably have a cheatsheet available. 

```
$ sudo debugfs -R "stat <1521431>" /dev/DRIVENAME
```

There is a lot shown in the output, but the only thing that matters to us right now is the block number, labeled as "Blocks:" or "Extents:"" with a numeric value, for example, "547473". If the file is large enough you might get multiple Extents or Blocks, in which case things get more complicated.

Whether it says Blocks or Extents, save that number. It is the number of blocks from the start of the drive that the file is located at.

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

# Metadata

Metadata is the information about a file, rather than the data contained in the file. Most file formats have room for metadata towards the front of the file, which means that the metadata for the file is stored inside of the file, but is not considered to be part of the file itself. It is possible to remove the metadata for the file without affecting the way the file displays. To find information about metadata for a specific file format, check the RFC. To pull the metadata from a file, use a tool for it, like this one: <http://exif.regex.info/exif.cgi> 

Check out the metadata for this file: <https://raw.githubusercontent.com/ianare/exif-samples/master/jpg/gps/DSCN0029.jpg>

Another type of metadata is filesystem metadata. Rather than being included in the file itself,  it is stored in the inode table. Use ```ls -i``` to get the inode information for a file and then use ```debugfs -R "stat``` like we did above to get all the information for the file, including the filesystem metadata.

A third type of metadata is information about who sends and receives information. Even if the content can't be decrypted, just knowing who sends to who is useful information and can be dangerous depending on the context. This [article from the EFF](https://www.eff.org/deeplinks/2013/06/why-metadata-matters) is great.

# Assignment

```markdown
Questions:

1. Where are drives located on Linux?
2. Explain how the inode table is used to find saved files in a few sentences.
3. What happens when you delete a file in a few sentences.
4. What is metadata? 

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
