# Basic Bash Scripting
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
Bash has a built in scripting language, which I guess is pretty cool. These days, you should just use Python for most things instead of writing Bash scripts, but you would be horrified if you knew how much of the internet, nay, how much of the world runs on bash scripts. Most servers? Of course. Water plants? Absolutely. Nuclear reactors? I'd be shocked if there wasn't a cron-jobbed bash script running somewhere in every plant in the world. Don't tell anyone, but a great deal of this site runs on janky cron jobs. 

Because bash and cron jobs (which we'll learn about later) are basically the underpinning of the modern world, you should probably get to know them. 

## Bash Scripts

Open up your favorite text editor and build a file that looks like this and save it as "hello.sh". Note the top line which tells the shell what type of script it is, the file extension doesn't matter at all.

```
#!/bin/bash
echo "Hello World"
```

Then you can execute it using the command ```$ bash hello.sh```. Similarly, you can use chmod to mark the file executable and then execute it using ```$ ./hello.sh```.

As you might have noticed, the command you are running is exactly what you would run in a normal terminal command. Does that mean most of the knowledge you've learned remains applicable in here? 

In a shocking turn of events, yes, it does. Don't get used to things working this nicely  in the future.

## More Advanced Scripting 

Check out what we can do to take input and execute commands in a script. Just build the script, save it whatever you want, make it executable and run it. Don't worry about understanding it, I'm trying to demonstrate capability, not teach you how to do things at this point. 

```
#!/bin/bash
echo "Enter Your Name"
read name
# read is a nice little bash builtin function that isn't available in the shell, 
# but is in the scripting language. Also, lines starting with '#' are known as comments and aren't executed, these are in all languages, you'll get used to them.
date="$(date)"
# We just set the value that date returns to date
# using something called "command substitution". 
# Unsurprisingly, you can do very complicated things with that.
echo "Welcome $name it is $date"
```

And finally, here is a program that counts to 10, printing out all the numbers as it goes.  Save it as counter.sh in your Documents directory and run it with ./counter.sh.

```
#!/bin/bash
valid=true
count=1
while [ $valid ]
do
echo $count
if [ $count -eq 10 ];
then
break
fi
((count++))
done
```

Don't worry about what is going on in there, just know we can do whatever we want using bash scripting, though we probably should use something more modern like Python. Still, good to have in a pinch.

## Cron Jobs

Sometimes you might find yourself needing to run a command every couple of minutes, and luckily, there is a wonderful Linux tool for that named crontab. These commands can be anything, from kicking off shell scripts, starting python processes, checking that programs are still running, really anything you want to schedule, cron jobs are the right way to do it.

A crontab file contains instructions for the cron daemon in the following simplified manner: "run this command at this time on this date". Each user can define their own crontab file. Commands defined in any given crontab are executed under the user who owns that particular crontab.

To see what is in your crontab file, run ```crontab -l```. To edit it, run ```crontab -e```.

Add this to the bottom of your cronjobs to execute the counter.sh script every minute. 

```*/1 * * * * /home/studentName/Documents/counter.sh```

Alright, that incantation on the front that says when to run can be a monstrosity, especially when it comes to more complicated timing, so don't learn it and just use existing examples on line. I use this site (https://crontab.guru/examples.html) for all my crontab-ing needs. (You better believe that Roppers run on crontabs and janky Python scripts).

# Assignment:

1. Write the bash script to append the date and time the script was run to a file named "dates.txt" 
2. Write the cron command to run the script you just wrote every Friday at noon.

Answer in the usual format. 

```
 Answers:

 1.

 Resources:
 

 Pre-Questions:


 Post-Questions:


 Feedback:

```


##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->