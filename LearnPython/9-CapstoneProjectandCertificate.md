# Capstone Project and Certificate
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
We generally know how to scrape a website now, and hopefully have a good feeling about our ability to program in Python. We also learned about Linux and completed the first half of the Bandit CTF. 

What better way to bring it all together than to write a python script which solves a couple of the Bandit challenges for you? 

The assignment is as follows: 

Write a python program that takes a text file as configuration input. This text file should be in JSON format. The first configuration file will be named "bandit1.cfg" and should contain the following:

* Address: bandit.labs.overthewire.org
* Port: 2220
* Username: bandit0
* Password: bandit0

As well as all commands required to solve the level.

The script, upon taking in the config file, should SSH into the level using the supplied password, then runs the required command(s) to find the password for the next level. After identifying the password, the script should save it to a separate text file named "passwords.txt", along with the level it goes to.

From there, the script should then take in the configuration file for the next level, "bandit2.cfg". This config file should be in the same format as the first, but instead of providing the password, use the password saved in "passwords.txt". Then log in to the level, run the commands required, and save the password for the next level to "passwords.txt".

Do this for levels 0-5. Your final project should include a python file, six .cfg files, and a README explaining usage. None of these files should include passwords outside of the password for bandit0.  

This is a complicated project and you will have to use Google, some of your existing code, and the #python channel in Slack. As you go along, we will be there to help you out!

Once you have it working, submit a link to your Github repo to d.m.devey@gmail.com and to the text box below.

# Notes 
1. I recommend you use [this library named Pwntools](https://github.com/Gallopsled/pwntools-tutorial/blob/master/tubes.md). 


Good luck!! When you are done, I'll send you the Ropper's Python certificate and you will basically be done with this course!
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->