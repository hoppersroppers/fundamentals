# Basic Principles

[Check out our free CTF Course!](https://academy.hoppersroppers.org/mod/page/view.php?id=564) 

## Flag Format

Most of the time the flag format will be an ASCII string that you discover during the course of the problem.

In the most common scenario it will look something like "The Flag is: this_is_the_flag", "ctfName{this_is_the_flag}"" or just "this_is_the_flag". Sometimes the organizers will use leetspeak so it will look like "ctfName{th15_15_th3_fl4g}"". Of course not all flags can follow these formats, so always be looking for anything out of place, especially during forensics challenges.
Most problems will specify the flag format, but if they do not, you must be on the lookout for any ambiguity.

Always check for:

* Capitalization
* Character encoding
* Trailing whitespace/newlines
* Date/Time formats
* Hex address formats (0x0042 vs 0042 vs 00000042) 

Sometimes the flag will require you to submit a hash of a variety of information that you have found. Be especially careful with these problems to verify what you are putting into your hashing algorithm, and that you are using the right algo.

Very rarely is a flag able to be brute forced. As a result, even if the potential number of solutions is small, expect that there is a twist or mis-spelling that will require you to solve the problem. Most CTFs will specifically have a rule against brute forcing in their rules because of the potential impact on the event infrastructure, so just solve the problem, don't bruteforce.



## Mechanics

Some common mechanics for Jeopardy-style CTFs:

Just like Jeopardy, the more difficult problems are worth more points, and the easier or higher-variance trivia and guessing problems worth fewer points. This encourages people to look at the difficult problems and learn the more hardcore security skills!

Therefore, any CTF scoring system--however complex--must strongly tend to reward the teams that demonstrate the best security skills. Think hard on your game mechanics, and try to keep them from being exploitable or distracting too much from the core challenges. (Not that that can't be fun, but little in this document would apply to such a competition!) 

Some common mechanics for Jeopardy-style CTFs:

1. Often solving the easier challenges will unlock harder, higher point challenges.
  * Binary Exploitation problems wind up having some of the highest general point values because they are the most difficult skills to learn.
2. There are usually extra "first blood" points (usually only a small number that allow for tie-breaking)  given to the first few teams who solve a challenge. This discourages "flag hoarding", where a team holds on to their flags and submits them all at the very end of the competition.
   * (This is a fairly advanced move, but flag hoarding allows a team to hide their true score on the scoreboard, causing other teams to feel that they have comfortable leads and don't need to be working to the last minutes. Then the flag hoarders can drop their stored flags and pull ahead in the last few seconds. Awesome when you do it, pretty terrible when it is done to you.) .


## Communication 

Organizers are usually reachable throughout the entire CTF, either in an IRC, Slack, or by email. With that said, you should never reach out to organizers for hints during the competition. However, if a challenge appears to be failing or a webserver is not responding, you should let them know so that they can take action behind the scenes to make sure everything is operating as designed. 

Organizers also usually have an official, non-real time channel like a Twitter or a news page on the site to ensure that nobody misses any important game updates. Sometimes hints are dropped their too. Whenever a change is made to a problem, usually it is announced in whatever the non-real time channel is, in addition to in the real time chat. When this happens, make sure to check the problem description for a change, and if a file has been updated, your first move should be diffing the two files to find what was "fixed". Most of the time that will help you find your answer.



## References:
* <http://captf.com/maxims.html>
* <https://github.com/pwning/docs/blob/master/suggestions-for-running-a-ctf.markdown>
[Visit the course page!](https://academy.hoppersroppers.org/mod/page/view.php?id=564) 
