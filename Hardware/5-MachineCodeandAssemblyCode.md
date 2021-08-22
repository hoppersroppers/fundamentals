# Machine Code and Assembly Code
##  [Register for the Free Course Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
In order to be executed on a CPU, code must be written in a way that is understood by the CPU. This is called 'Machine Code' and consists of 1s and 0s. As a note, there are various families of CPU "architectures" which require different machine codes to operate properly. Don't worry about this now.

[<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Von_Neumann_Architecture.svg/800px-Von_Neumann_Architecture.svg.png">](https://wikipedia.org)


Humans don't like 1s and 0s as much as computers so we prefer to abstract ourselves away from the bits as far as possible. We do this what are called "assembly" languages, which is a defined syntax of instructions that map desired outcomes to the binary machine code the CPUs run off of. An assembler is a piece of code written for a specific type of CPU that does a 1 for 1 translation of assembly code into binary that can be executed.

I like this video: 

<iframe width="560" height="315" src="https://www.youtube.com/embed/wA2oMRmbrfo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Assemblers do a 1 for 1 translation from assembly to binary, but what if we are looking for something that can optimize or simplify the work needed to be done by the programmer? Basically, programmers don't want to write assembly all day if they can write in a higher-level language that abstracts away even more of the complexity involved with dealing with CPUs. To do that we would need something called a "compiler". 

A compiler is a computer program that translates computer code written in one programming language (the source language) into another programming language (the target language), almost always assembly. This allows the programmer  to write in a human-friendly language like Python, C, or Java, and then convert it to assembly to run. This saves huge amounts of time and allows developers to spend more time doing and less time working. Don't worry too much about how all this works, just understand that it does. It's a bit more advanced than we need, I just want you to be aware of it.

As an example, here is a simple program that prints out "hello, world" in C, assembly, and machine code.


### C
```
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
```

### Assembly 
```
    global  _main
    extern  _printf

    section .text
_main:
    push    message
    call    _printf
    add     esp, 4
    ret
message:
    db  'Hello, World', 10, 0
```

### Machine Code 
``` b8    21 0a 00 00   
a3    0c 10 00 06   
b8    6f 72 6c 64   
a3    08 10 00 06   
b8    6f 2c 20 57   
a3    04 10 00 06   
b8    48 65 6c 6c   
a3    00 10 00 06   
b9    00 10 00 06   
ba    10 00 00 00   
bb    01 00 00 00   
b8    04 00 00 00   
cd    80            
b8    01 00 00 00   
cd    80            
```

We are all agreed we would prefer to write in C and not machine code, right?

Read [this about our namesake Grace Hopper and the first compiler:](https://web.archive.org/web/20210304184039/https://history-computer.com/grace-hopper-history-of-the-first-compiler-a-0-system/)

Then watch this: 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IhC7sdYe-Jg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Some day, you might write a compiler so all of the things you just learned about makes more sense to you. Or you can not do that. You don't get as much out of it as people say you would.

What we just went over was just the absolute basics of computer hardware and logic. I did not spend any time on machine code, assembly or memory, and you WILL get destroyed by it the first time you see it. 

My recommendation, avoid anything involving machine or assembly code until after you have spent some dedicated time on the subject. Most people can go their entire careers in security without having to touch assembly. That is a good thing. The only people who really have to deal with this bullshit are reverse engineers, exploit developers, and a few other specific jobs done by people who hate themselves. 

To translate this, don't try to jump into any Reverse Engineering problems, for now. Take our [Fundamentals of Reverse Engineering]($@COURSEVIEWBYID*4@$) course when you feel the urge, but for now, just move on. 

Assignment:

1. Describe machine code and assembly. 
2. What was Grace Hopper's primary contribution to computing?
##  [Click Here to Start Learning Today!](https://roppers.thinkific.com/courses/computing-fundamentals)
<br><div id="mc_embed_signup"><form action="https://gmail.us5.list-manage.com/subscribe/post?u=4d03cc5db483966f7e0fe17cc&amp;id=8d9620c4b7" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>  <div id="mc_embed_signup_scroll"><h2>Join our mailing list to get updates about our courses and our organization!</h2><div class="indicates-required"><span class="asterisk">*</span> indicates required</div><div class="mc-field-group">	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span></label>	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL"></div>	<div id="mce-responses" class="clear">		<div class="response" id="mce-error-response"style="display:none"></div>		<div class="response" id="mce-success-response" style="display:none"></div>	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_4d03cc5db483966f7e0fe17cc_8d9620c4b7" tabindex="-1" value=""></div>    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>    </div></form></div><script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script><script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = newArray();fnames[0]="EMAIL";ftypes[0]="email";}(jQuery));var $mcj = jQuery.noConflict(true);</script><!--End mc_embed_signup-->