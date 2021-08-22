# Permissions and Umask
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
When a file is created in Linux, the default permissions for it is "666". For a directory, the default permissions are "777". That is basically always fine, but if you need to for some reason, you can modify the default permissions using a command named ```umask```. 

# Masks

Okay, things are about to get a bit weird. You saw a little bit of binary addition in the tutorial and hopefully that made some sense. Now, you're going to learn about masks, which are a completely different thing than binary addition. To avoid getting confused, keep in mind that masks and binary addition have nothing to do with eachother, besides all the 1s and 0s.

Masks are all over computing and generally can be defined as strings of bits that set other bits based on logic. This logic is based on the Digital Logic Gates we learned about in the "Digital Logic" section.

Depending on the required implementation, different logic gates can be used for different masks. This means that the logic for a gate can be "AND", "OR", "XOR"... long story short, don't think of masks as any specific thing, just read what the logic is for that specific scenario and reason about that in your head. 

One of the more common uses of masks we see in Linux is for controlling default permissions. 

```
EX.1
  Binary:  6 6 6   // 110 110 110 
  Mask:    0 2 2  // 000 010 010
  Output: 6 4 4 //  110 100 100

EX.2
  Binary:  7 7 7 // 111 111 111
  Mask:    0 4 2 // 000 100 010
  Output: 7 3 5 // 111 011 101

```  

Hopefully this makes sense. Honestly, you won't use this much, but it is good to know about.

The most common place where you will see permissions masks is with the ```umask``` command. Run it now and you will see what your shell's default masks are.

Now make a new file and use ```ls -l``` to see what the permissions are. Do they match?

In order to change your permissions that files default to for your shell:

```
$ umask 002
```

This umask of "002" converts over to being a mask of "775". 

When applied to This will change permissions so that files come out RWX for user and group and R for other, but don't just believe me, test it out.

You might have noticed that when you ran ```umask``` the first time there was a leading "0" in front of the other numbers. That first bit is the special bit we talked about earlier in terms of the "sticky bit". There are other special types of files that can be indicated in the special bit location, but don't worry about them for now.  

For your assignment, discuss which bitwise operation is occurring when the masks is applied. Answer in the appropriate format. 

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