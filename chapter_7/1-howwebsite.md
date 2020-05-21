# How Website

[Check out our free CTF Course!](https://academy.hoppersroppers.org/mod/page/view.php?id=627)

We assume you already generally understand how the internet and websites work. If not, read these resources over.

* <https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work>
* <https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works>
* <https://www.lifewire.com/what-is-a-web-application-3486637>

## Error Codes
* Things break a ton during WebEx and you should know how they are breaking. Memorize the basics about common error codes!
<https://www.digitalocean.com/community/tutorials/how-to-troubleshoot-common-http-error-codes>

1. What do codes 200-299 mean?
2. What do codes 300-399 mean?
3. What do codes 400-499 mean?


## Google Hacking
What is Google hacking (or Google dorking) ? Well, Google (and other search engines)  are built around a large number of web-crawlers that are constantly scraping the internet. They scoop up everything that is publicly available and index it, allowing you to search it. However... what happens when the web crawlers find something that they shouldn't?

Play around with a few of these Google hacks on Exploit-DB:

* <https://www.exploit-db.com/google-hacking-database>
* Don't break any laws while doing it, but it is a lot of fun seeing what is available online.


In order to prevent Google and other search engines from indexing a site, many sites use a robots.txt file to "block" the web crawlers. Robots.txt files are not actually part of an RFC yet, despite being an accepted part of the internet for years, but Google has recently proposed the Robots Exclusion Protocol as an official standard under Internet Engineering Task Force . Importantly, robots.txt are meant to be a good faith request by site administrators, and are regularly ignored by web crawlers. This means that any web crawler, or you, can visit a site's robots.txt and quickly identify any part of the site that the owner does not want crawled.

This often comes up in CTF problems, so it is always worth a quick check.
[Visit the course page!](https://academy.hoppersroppers.org/mod/assign/view.php?id=627)
