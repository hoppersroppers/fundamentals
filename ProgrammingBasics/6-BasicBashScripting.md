# Basic Bash Scripting

Bash has a built in scripting language, which I guess is pretty cool.
These days, you should just use Python for most things instead of
writing Bash scripts, but you would be horrified if you knew how much of
the internet, nay, how much of the world runs on bash scripts. Most
servers? Of course. Water plants? Absolutely. Nuclear reactors? I'd be
shocked if there wasn't a cron-jobbed bash script running somewhere in
every plant in the world. Don't tell anyone, but a great deal of this
site runs on janky cron jobs.

Because bash and cron jobs (which we'll learn about later) are basically
the underpinning of the modern world, you should probably get to know
them.

## Bash Scripts

Open up your favorite text editor and build a file that looks like this
and save it as "hello.sh". Note the top line which tells the shell what
type of script it is, the file extension doesn't matter at all.

``` default
#!/bin/bash echo "Hello World"
```

Then you can execute it using the command `$ bash hello.sh`. Similarly,
you can use chmod to mark the file executable and then execute it using
`$ ./hello.sh`.

As you might have noticed, the command you are running is exactly what
you would run in a normal terminal command. Does that mean most of the
knowledge you've learned remains applicable in here?

In a shocking turn of events, yes, it does. Don't get used to things
working this nicely in the future.

## More Advanced Scripting

Check out what we can do to take input and execute commands in a script.
Just build the script, save it whatever you want, make it executable and
run it. Don't worry about understanding it, I'm trying to demonstrate
capability, not teach you how to do things at this point.

\#!/bin/bash  
echo "Enter Your Name"  
read name  
\# read is a nice little bash builtin function that isn't available in
the shell,  
\# but is in the scripting language. Also, lines starting with '#' are
known as comments and aren't executed, these are in all languages,
you'll get used to them. 

date="$(date)"  
\# We just set the value that date returns to date  
\# using something called "command substitution".  
\# Unsurprisingly, you can do very complicated things with that.  
echo "Welcome $name it is $date"

And finally, here is a program that counts to 10, printing out all the
numbers as it goes. Save it as counter.sh in your Documents directory
and run it with ./counter.sh.

\#!/bin/bash  
valid=true  
count=1  
while \[ $valid \]  
do  
echo $count  
if \[ $count -eq 10 \];  
then  
break  
fi  
((count++))  
done  
  
Don't worry about what is going on in there, just know we can do
whatever we want using bash scripting, though we probably should use
something more modern like Python. Still, good to have in a pinch.

## Cron Jobs

Sometimes you might find yourself needing to run a command every couple
of minutes, and luckily, there is a wonderful Linux tool for that named
crontab. These commands can be anything, from kicking off shell scripts,
starting python processes, checking that programs are still running,
really anything you want to schedule, cron jobs are the right way to do
it.

A crontab file contains instructions for the cron daemon in the
following simplified manner: "run this command at this time on this
date". Each user can define their own crontab file. Commands defined in
any given crontab are executed under the user who owns that particular
crontab.

To see what is in your crontab file, run `crontab -l`. To edit it, run
`crontab -e`.

Add this to the bottom of your cronjobs to execute the counter.sh script
every minute.

`*/1 * * * * /home/studentName/Documents/counter.sh`

Alright, that incantation on the front that says when to run can be a
monstrosity, especially when it comes to more complicated timing, so
don't learn it and just use existing examples on line. I use this site
(https://crontab.guru/examples.html) for all my crontab-ing needs. (You
better believe that Roppers run on crontabs and janky Python scripts).

If you want to spend more time learning about Bash, check out
<https://tryhackme.com/room/bashscripting> , but promise to come back to
Roppers.

# Assignment:

1.  Write the bash script to append the date and time the script was run
    to a file named "dates.txt"
2.  Write the cron command to run the script you just wrote every Friday
    at noon.
