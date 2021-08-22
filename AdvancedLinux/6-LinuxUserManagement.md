# Linux User Management
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
While being a system administrator covers a ton of responsibilities, potentially the most important on the day-to-day is User Management. As people come and go from a network, passwords are forgotten, the organization structure changes and the sysadmin rules over all and ensures everyone has the permissions they need, and perhaps more importantly, doesn't have any permissions they don't need. We manage these using Users and Groups in Linux. 

The Operating System maintains the distinctions between Users and between Groups for us, but as sysadmins, we have to tell the OS what to do. The security provided by the OS is only as good as we define it, so if our permissions we tell the OS to enforce are incorrect, we can have no security at all. 

Users are differentiated and monitored by the OS according to User ID (UID). Groups are identified using, you guessed it, Group ID (GID). When we attempt to open a file or a directory, the permissions for the file are checked against our UID and GID. If all the checks pass, we are given access. 

As your normal user you can use ```cd``` to enter the \home directory to view your user directory. You can also back out into root and attempt to read the \root directory with ```cat```. As you are not root and do not have the permissions, this will fail. 

Check out the permissions of the directories in ```/``` using ```ls -l``` and see why.

##  /etc/passwd 

While usernames are used in the human-visible interface for computing, behind the scenes, the OS operates using the User IDs (UIDs) we already talked about. As different operations occur, the OS checks these UIDs against a file that is represented in the Linux filesystem as /etc/passwd. All of these files can not only be viewed, but can be edited if you have the appropriate permissions. On rare occasions you might go into these files in 'vim' to make edits.

To view:
```
$ cat /etc/passwd
```

Here you will see a printout of all the users with accounts on your computer. The top one will be 'root', and will look like generally like this.
```
root:x:0:0:root:/root:/bin/bash
dennis:x:1337:1337:Dennis:/home/dennis:/bin/bash
```

There will be many more entries than this, but let's ignore them for now. 

We will learn about how this file is broken down using ["man passwd"](https://linux.die.net/man/5/passwd)

To break it down, /etc/passwd stores data about users separated by colons (:). 

1. User name
2. Encrypted password 
   * On modern systems, the password will not be stored here and is indicated by an 'x'. We will learn about where the passwords are stored next.
3. User ID number (UID)
4. User's group ID number (GID)
5. User full name and other data(GECOS) 
   * This is an arbitrary set of data also known as the "comment" field. Sometimes name, email, phone number, separated by commas. Most of the time, there is nothing here but your name.
6. User home directory
7. Default Login shell

## /etc/group

Similar to /etc/passwd, this prints out information about the various groups on the computer. 

roppers:*:1337:dennis, grace


1. Group name
2. Group password - Using an elevated privilege like sudo is standard, but a separate password can be added. "*" will be put in place as the default value.
3. Group ID (GID)
4. List of users - Manually specified users in the group

## Add a User and Set the Password

```
$ sudo useradd -c "User's Full Name" account_name
$ sudo passwd account_name 
```

## Delete an Account 

To delete an account:
``` 
$ userdel -r account_name
```
Userdel with the "-r" flag is final and will delete the user along with the user's home directory. Make sure you want to do this before running the command. 

[<img src="https://imgs.xkcd.com/comics/letting_go.png">](https://xkcd.com/215/)

## Set Passwords

While usually you will use ```passwd``` to set passwords, there are many other uses. To check the status of a user account, use this format.

```
$ passwd -S account_name
```
You can also do more complicated things using the command, but google for a cheatsheet to do that, or if you don't have internet access, use man pages. 


# Assignment: 

1. Break down  this entry from /etc/passwd. Describe each field. 
   * ```dennis:x:1337:1337:Dennis:/home/dennis:/bin/zsh```
2. What does this ```passwd``` command do? Work through each argument on a separate line.
   * ``` $ sudo passwd -n 1 -x 120 -w 4 -i 10 dennis ```
3. Create a new account, set the password, check the account in /etc/passwd. Delete the account. Check /etc/passwd again. Briefly write up what you saw and any problems you had doing this.

Answer in the appropriate format. 

```
 Answers:

 1.

 Resources:
 

 Pre-Questions:


 Post-Questions:


 Feedback:

```
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
