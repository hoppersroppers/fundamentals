# Linux Self Defense
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
