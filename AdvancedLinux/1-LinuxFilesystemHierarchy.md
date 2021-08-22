# Linux Filesystem Hierarchy
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
[<img src="https://imgs.xkcd.com/comics/porn_folder.png">](https://xkcd.com/981/)

Previously we talked about how files are saved in Linux, and we've spent some time making directories. However, we have been generally fairly constrained in our working directory, and it is time to learn what the world outside of our user's directory looks like. 

This world is organized according to what is known as the Linux Filesystem Hierarchy Standard (FHS). 

The FHS is maintained by the Linux Foundation, and much like a lot of the other standards we have talked about is a recommended standard so that code written for one Linux distribution will be cross-compatibile with another. Primarily, the FHS is a way of organizing user, program, and system files in a tree-like hierarchy, which makes it easy for us to install, uninstall, and find specific files. 

# Important Directories

### '/' aka Root 

Our tree starts from '/', the root. No matter what device a file is on, it will be accessible from the root directory. Root is the highest level of the hierarchy and everything falls underneath it. To access root, we use the representation ```/```. Right now, cd into root. 

From there, run ```ls``` to see the available directories. 

### Root Directories 

Read through [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](this link) and click through the files a bit to get an idea of what is going on in each of the root directories. 

If you do not have internet access, you can access information on the FHS with ```man file-hierarchy``. 

This is a weird part of Linux as what we see today is the end result of years and years of design tradeoffs, historical reasonings, and heated debates. A few directories don't really make sense anymore, a few things are brand new. All of this is critical in the "In Linux, everything is a file" philosophy. 

For your assignment, describe the following directories and what is saved in them. If there is anything notable about the use of the directory, or how the permissions are applied, please include that. 

I expect you to have a large number of Pre-Questions for this assignment, and it will take you a reasonably long time. Don't beat yourself up too hard about this, but instead use it as a way to assess your current understanding and fill in your gaps. If anything is completely foreign to you, let me know in your feedback and in #feedback.

1.  ```/```
2. /root
3. /boot
4. /bin and /sbin
6. /etc
7. /home
8.  /lib
9. /usr 
10.  /var
11. /tmp and /var/tmp
12.  /dev
13. /mnt and /media
14. /proc and /sys

Please respond in the appropriate format:

```
 Answers:

 1.

 Resources:
 

 Pre-Questions:


 Post-Questions:


 Feedback:

```

I know this is a longer assignment but it is very important. 

##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->