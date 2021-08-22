# Capstone Project and Certificate
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