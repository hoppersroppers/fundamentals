# Linux Self Defense
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
[<img src="https://imgs.xkcd.com/comics/linux_user_at_best_buy.png">](https://xkcd.com/272/)


Before we get into security, let's talk about risk.

 Risk = (Threat x Vulnerability) * Asset Value 

* Threat =
* Vulnerability = 
* Threat * Vulnerability =

The addition of asset value lets us get a much better idea of what the impact would be.


What do you want to protect? Who do you want to protect it from? How likely is it that you will need to protect it? How bad are the consequences if you fail? How much trouble are you willing to go through in order to try to prevent those?

So back to what we have been doing, Linux is generally known as "safer" than Windows in terms of malware because there are less people targeting it. But let's 
 break that down to the two major ways we have to worry about getting hacked. 

1. You run some malicious program on your computer
2. A remote exploit is used against your computer

That means that the "threat" is less. And there is an argument that Linux has less "vulnerabilities" largely because there is less remote surface area of most Linux boxes, and more importantly less people browsing the internet. 

That is generally true, but you should always be careful and never assume you will be safe downloading random things and running random commands. I talk about it much more in the Security Fundamentals course, but you are trying to become a harder target that doesn't get hacked by a random automated script or someone who sees you left your computer lying around, not a uber hacker who can withstand a foreign government trying to steal their files.

Back to the more technical side, we've talked about a few sort of security things, but I am going to bring them all back together here and then add a few more basic hardening tips.

Use Strong and Unique Passwords
Update Your Software Regularly
Enable Automatic Updates
Make Backups
Check Listening Network Ports
netstat -tulpn

Disable root Login
No empty passwords
# awk -F: '($2 == "") {print}' /etc/shadow
Password Poliicies

No UID 0
# awk -F: '($3 == "0") {print}' /etc/passwd

 Disable root Login



<https://www.cyberciti.biz/tips/linux-security.html>
<https://www.linuxtopia.org/LinuxSecurity/index.html>
<https://www.computerworld.com/article/3144985/linux-hardening-a-15-step-checklist-for-a-secure-linux-server.html>
<https://opensource.com/article/19/10/linux-server-security>

##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->