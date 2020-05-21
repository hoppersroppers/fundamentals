# Things You Shouldnt Try to Do

[Check out our free CTF Course!](https://academy.hoppersroppers.org/mod/page/view.php?id=623) 

Remember what we said earlier about how math will win, every time? 

The corollary to the rule that you cannot beat math is "Never roll your own crypto". <https://www.vice.com/en_us/article/wnx8nq/why-you-dont-roll-your-own-crypto>. Anybody can write their own crypto libraries, but it probably sucks and is susceptible to attacks that were known in 1942. So when you see a CTF challenge with a "custom encryption library", know that whoever wrote that library implemented it wrong.  In order to solve that challenge, you will need to know a great deal more about crypto than this course will try to teach you. If you want to become very very good at crypto, do the Matasano CryptoPals challenges. <https://cryptopals.com/> and spend the rest of your days reading academic papers. Otherwise, just move on with your life. 

So moving on, if implemented properly (and the assumption for all standard libraries is that they are) , the attacker will not beat math. It doesn't matter if you spin up a cloud server or build a facility in Utah, you're not going to beat math.  Anytime you find yourself trying to do any of these things, assume that you have gone wrong somewhere along the way.


1. Reverse a hash
   * If nothing comes up when you google for it, move on. This is not what you are supposed to solve.
2. Create a hash collision
    * Possible for MD5 and SHA1 in various ways. Read this for more info: <https://github.com/corkami/collisions>  
3. Crack a password that is longer than 8 characters
   * The math just isn't there. You are missing something.
   * That something might just be a wordlist gathered from all words on a website/server/description
4.  <https://en.wikipedia.org/wiki/Halting_problem>
5. <https://en.wikipedia.org/wiki/P_versus_NP_problem>
[Visit the course page!](https://academy.hoppersroppers.org/mod/page/view.php?id=623) 
