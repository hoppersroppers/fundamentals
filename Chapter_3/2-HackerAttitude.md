
# Ropper's How to be a Hacker
Written for the [Roppers Computing Fundamentals](https://academy.hoppersroppers.org/course/view.php?id=8) course
By Dennis Devey

## Why This Document?

If you spend enough time in a position of some sort of authority online, people will regularly ask you "how can I become a hacker?" For the last year I've run a website named [Hopper's Roppers](https://www.hoppersroppers.org/index.html) that provides free security education and I seem to get asked this once a month. The canonical answer for many years was a document written by a man named ESR, who was a pioneer in the open source community. The Hacker-How-To, as this guide is known, is a good resource but is not written in a way that is accessible to a beginner, and has far too much jargon in it. I believe that a guide for beginners should be readable by beginners and not require years of computing experience to understand. Also, ESR is an asshole, and I don't like having new students' first interaction with the hacker community to be with an asshole. So, I wrote my own.

## What Is a Hacker?

The internet is filled with definitions of the word 'hacker', but there are really only two that matter.

As defined by the [Internet Users' Glossary](https://tools.ietf.org/html/rfc1392), a hacker is "a person who delights in having an intimate understanding of the internal workings of a system, computers and computer networks in particular." This word originated with some folks at MIT and spread throughout the earliest groups of people hooked up to what would eventually become the internet. Rather than operating at the surface level of a system, a hacker gets deep inside it, pokes and prods it, figures out how it works, and then figures out how to make the system do something with that knowledge. The vast majority of people who identify as hackers are skilled programmers, especially ones who work on open source projects, but hacking does not only apply to computers and networks and code, but also things like "life-hacks" or hacking government policy. What makes something hacking is up to you and the people you are sharing your hacks with. For this course, we focus on building the skills and mentality required to hack with, in, on, and around computers, but you'll also find yourself looking at the world through different eyes.

The other definition for hacker, and the more popularly used one, is "people who break into computers". At one point there was a battle for control of the word hacker, and the hackers who build things wanted the people who break things to be named 'crackers'. Well, the builders lost, and now 99% of the time when you hear the word hacker, it's in relation to infosec. 'Hacker' is in the process of being reclaimed by the good guys, and now most of the new generation wears it with pride.

Roppers is here to teach you how to delight in understanding the inner workings of the system you are breaking into (or defending), with a focus on having the right attitude and a strong sense of ethics. We try to bridge the line between the hacker community and the infosec community, but you get to be the judge of how well we do it.


# The Hacker Attitude

1. The world is full of fascinating problems waiting to be solved.
2. No problem should ever have to be solved twice.
3. Boredom and drudgery are evil.
4. Freedom is good.
5. Attitude is no substitute for competence.

Hackers build things, and occasionally break things, and sometimes build things to break things. There is no universal set of agreed upon rules that hackers follow, but The Hacker Attitude is a good starting point. As I like to say, any framework is better than no framework at all.

## 1. The world is full of fascinating problems waiting to be solved.

The defining aspect of being a hacker is that when a problem is identified in a system, whether it is a computer or in society, a hacker will try to solve it by learning the system and applying that knowledge. Hackers have a bias for action and a bias towards learning. There is no expectation that a hacker knows the answer when they look at a problem for the first time, but rather that they will methodically work through it using the knowledge and skills they have.

From the original Hacker-How-To: "You also have to develop a kind of faith in your own learning capacity — a belief that even though you may not know all of what you need to solve a problem, if you tackle just a piece of it and learn from that, you'll learn enough to solve the next piece — and so on, until you're done."

## 2. No problem should ever have to be solved twice

The idea behind this point is that as a society, humans have been slowly moving away from hunting and gathering since we learned how to pass information to each other. As knowledge was created, it was shared and passed on to improve the lives of others. In modern times, hackers get to sit on computers in air conditioned rooms and work on solving problems that their ancestors wouldn't have dreamed of.

As most people believe that the progress of humanity is important, when we solve a problem or create new information a hacker believes there is somewhat of a moral obligation to share the progress they have made with the widest audience possible. By solving problems shared by other people, and especially other hackers, you free them up to work on new and even more exciting problems. Open source software lies at the heart of the modern world, having been created and largely given away by hackers. By solving a problem shared by society you free others from worrying about that problem. By solving a problem shared by other hackers, you free them to work on other problems.

"No problem should ever have to be solved twice" does not mean that there is no reason to reimplement something or do it slightly better. If someone wants to write a better email client, they certainly can and should, as it will make the entire ecosystem better. What is a concern to the hacker is artificial barriers to progress, usually built by bureaucracy or the pursuit of money, especially closed source code.

It is also important to note that there is no expectation you give all the software or information you create away, but there is the hope that a hacker will enable others to modify what they have created so that it provides the maximum benefit to as many people as possible, rather than maximizing profit.

## 3. Boredom and drudgery are evil
Along the same lines as before, hackers hate doing boring and repetitive work. This is, for the most part, true for all people. The world is full of fascinating problems, and the more people tied up doing drudge work, the less people there will be out there making the world a better place.

Along with sharing solutions to problems, hackers believe in automating the boring stuff so that everybody, especially other hackers, are free to work on what they want.

## 4. Freedom is good

This can also be rephrased as "Authoritarianism is bad". Freedom, for a hacker, is being able to fix the problems that they are most interested in fixing. Authoritarians do not allow the freedom to solve problems by creating rules and situations that cannot be worked around legally. When a system forces you to break the law or the rules in order to solve a problem, that system has become the problem.

While hackers are anti-authoritarian, that doesn't mean they are anarchists (though plenty are). All forms of authority have tradeoffs, and hackers work between the lines solving problems. But again, when a system doesn't allow a hacker to solve a problem due to censorship, secrecy, or coercion, it has become the problem.

## 5. Attitude is no substitute for competence

As you are just starting this journey, nobody is judging you for not knowing things, especially not here at Roppers. Questions are expected and you should spend more time confused than confident of what is going on. Our site exists to teach you, and more importantly, to guide you through this uncertainty as you take your first steps.

Some places in tech refer to themselves as a meritocracy, where individuals are judged based off of what they can do technically. This is problematic because meritocracy reflects and exacerbates pre-existing social inequalities, which in this case manifests as the amount of time spent exposed to and working with computers. Assuming competence is a function of how much time a hacker puts in, the person who has been able to spend the most time will be judged to be "better" in a system based on merit. F*** that. I'll promise you that if you put the time in, have the right attitude, and keep on pushing through, competency will follow. Soon you will have what it takes to hold your own with anyone, anywhere.

Competence is the end goal, but the only thing that counts at Roppers is having a positive attitude and a willingness to learn.


# Basic Hacking Skills

1. Learn how to program
2. Learn Linux
3. Learn how to use the internet and build a website
4. Learn to write effectively

We just went over the Hacker Attitude, and ended with arguably the most important for future success, "Attitude is no substitute for competence". There is a near infinite amount of tools and technologies that a technical person can learn, and we only have so much time, but here we identify the most important parts of the toolkit. Each of these items is taught in our introductory [Computing Fundamentals course](https://academy.hoppersroppers.org/course/view.php?id=8). We can't make you a hacker, but we'll point you in the right direction.

## 1. Learn how to program

Hackers must be programmers. The ability to turn thoughts into code and code into programs and then distribute those programs around the world is the most powerful thing that humans have ever had access to. When you start out you will be writing basic scripts and programs that have been written a thousand times over, but this is what you must build off of. What you will be able to accomplish will be based off of your strength as a programmer, and success will require a strong foundation.

While there are many languages, the best language for a beginner to learn is Python. It is clean, simple, and shockingly effective. It is not a toy to learn with but a fully featured language that is used by many of the largest companies in the world. There are piles of documentation and learning materials, and you will be skilled in it by the end of this course.

The more time you spend around computers the more languages you will find yourself exposed to. The next language you should learn, and this site will teach you, is C. Software written in C is the backbone of the internet and is known for its efficiency and speed... along with its complexity. There are always tradeoffs when you pick a language, but if you know Python and C you have the base you need to learn any other language. Eventually you will get to where you can learn a new language by taking the manual and using it to adapt the programming mindset you have to developed to a new syntax and style, but no rush.

True programming ability is not something that is learned from textbooks, but from reading and writing thousands and thousands of lines of code. Once again, it is going to take a lot of work, but this course will point you in the right direction. First, you will learn Python2, and then I will have you  program for the rest of the course in Python3, using the manual as a reference for the new syntax. You will do a variety of projects using modern development practices and end with a capstone that will challenge your skills.


## 2. Learn Linux

In a nod to the hackers of old, appreciate that we now have personal computers, as they had to work on shared machines the size of cars or larger. These early hackers worked with a series of operating systems, but the one that became dominant and has stood the test of time was named Unix.

There are a variety of operating systems in the world: Windows, macOS, some mobile OSs, and many Unix variants. Windows and macOS aren't open source which makes hacking on them difficult, while Unix variants are loved by hackers for its free and open source nature. Of the Unix-like operating systems, Linux is dominant, and of the Linux variants, Ubuntu is the most popular and easy to use for beginners.

It is easy to spend an entire lifetime on the internet without learning Linux, but that is not why you are here. You're here to become a hacker, and understand how things work, take them apart, and put them back together. Back in the day installing Linux was a major undertaking, but since then, hackers have written virtualization software that will allow you to run a "Virtual Machine" on your computer. You will spend plenty of time in the course getting Ubuntu installed and learning how to drive a Linux system, but in my opinion this is your most important step towards becoming comfortable with new and unfamiliar technologies.

## 3. Learn how to use the internet and build a website

While a lot of programmers make the world run anonymously, running trains and banks and power-plants, the internet is the most visible artifact of the world that hackers have been created. Consider the internet your birthright as a hacker and a human, and you are able to carve out a chunk of it and make it your own.

This doesn't just mean make a Twitter account, but that you can make your own website, host it online, and have it available for the world to visit. To do that you must learn HTML and CSS, the basics of Javascript, and how hosting works. By the time you complete this course you will have your own little slice of the internet, which I hope you fill up with more knowledge and more software to share with the world. (Take it from me, making the content and the website is the easy part... the hard part of the internet is getting people to read what you have to say)

## 4. Learn to write effectively

While previously written as "If you don't have functional English, learn it", I don't believe that is important anymore. 30 years ago when the entire world wasn't on the internet English might have been the default language, but these days there are enough people from everywhere that entire ecosystems can exist without having to ever talk outside of their native language. With that said, English is the working language of the internet, and the vast majority of documentation and conversation occurs in English. Luckily, thanks to advances in translation tools, it is very possible for someone who does not know English to participate online. In fact, many students of this site use translators for their homework or when posting discussions, and technology has advanced far enough that those posts are basically indistinguishable. (We also have dedicated channels in Slack for #roppers-Español, #roppers-Français, #roppers-Italiano, and #roppers-Deutsch)

Independent of the language that is being spoken, ensure that your language skills are good enough to be understood. Clear and concise writing is important, but poor grammar and misspellings will turn people off from helping you in many parts of the internet. At Roppers however, we are a judgement free zone, and won't hold it against you, especially for people who speak English as a second, third, or fourth language.



## Frequently Asked Questions

* Q: When do you have to start? Is it too late for me to learn?
* Q: How long will it take me to learn to hack?
* Q: Would you help me to crack a system, or teach me how to crack?
* Q: Where can I find some real hackers to talk with?
* Q: Can you recommend useful books about hacking-related subjects?
* Q: Do I need to be good at math to become a hacker?
* Q: What language should I learn first?
* Q: What kind of hardware do I need?

Q: When do you have to start? Is it too late for me to learn?

A: You should start as soon as possible, and hopefully during a period of time where you are free for a few hours a day to work. It is certainly easier when you are in middle and high school because then you have no responsibilities at all. There is no such thing as too late, but I certainly don't want you missing out.

Q: How long will it take me to learn to hack?

A: It really depends how much time you spend in front of a computer doing difficult and productive work. I'll say that at 1000 hours you should be pretty decent. This course will give you at least 100 and there's easily another 800 on the [Roppers Roadmap](https://www.hoppersroppers.org/roadmap/) to get you where you need to be. Spend some time doing CTFs and you should be good in about two years if you work for an hour or two a day. Of course, you can also spend four months doing it for 12 hours a day and that would work too.

Q: Would you help me to crack a system, or teach me how to crack? (Especially girlfriend/child's phone/computer/social media)

A: No. Don't break the law and definitely don't be an abusive piece of shit.

Q: Where can I find some real hackers to talk with?

A: Oh our Slack isn't good enough?

Hop on Twitter or go find some of the instant messaging channels out there. Personally I like:
* TheCyberMentor
* TryHackMe
* MalwareTech
* PwnSchool
* BlueTeamVillage
* RedTeamSec
* BlackHillsInformationSecurity

If you are looking for very beginner friendly spots I like:
* ManyHatsClub
* DeadPixelSec
* EternalNoobs
* Gatebreachers

If you are a veteran I recommend
* VetSec
* OperationCode
* VetCon

Q: Can you recommend useful books about hacking-related subjects?

A: I should do this. For where you are now, no books will help you more than these courses. Books are great for going deep, but if you are not doing the exercises, it is a lot like watching videos.

Q: Do I need to be good at math to become a hacker?

A: No. The most advanced stuff most people ever have to do is basic logic. That doesn't mean there aren't hackers who aren't great at math or use it daily, but luckily for us, those hackers wrote the code for us already and made it open source!

Q: What language should I learn first?

A: Python, then C, then Assembly. Follow the [Ropper's Roadmap](https://www.hoppersroppers.org/roadmap/), trust in the process.

Q: What kind of hardware do I need?

A: It really doesn't matter. My daily driver is an eight year old Dell laptop. Your only real concern is if you have a Chromebook which is locked down, but you can still get everything you need by using free cloud servers.
