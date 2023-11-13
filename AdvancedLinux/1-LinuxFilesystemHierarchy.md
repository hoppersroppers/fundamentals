# Linux Filesystem Hierarchy

 

## <a href="https://xkcd.com/981/" rel="noopener" target="_blank"><img
src="https://files.cdn.thinkific.com/file_uploads/429463/images/b6b/178/99c/1629595564249.jpg"
class="fr-fic fr-dii"
srcset="https://files.cdn.thinkific.com/file_uploads/429463/images/b6b/178/99c/1629595564249.jpg?width=1920 1x, https://files.cdn.thinkific.com/file_uploads/429463/images/b6b/178/99c/1629595564249.jpg?width=1920&amp;dpr=2 2x, https://files.cdn.thinkific.com/file_uploads/429463/images/b6b/178/99c/1629595564249.jpg?width=1920&amp;dpr=3 3x" /></a>

Previously we talked about how files are saved in Linux, and we've spent
some time making directories. However, we have been generally fairly
constrained in our working directory, and it is time to learn what the
world outside of our user's directory looks like.

This world is organized according to what is known as the Linux
Filesystem Hierarchy Standard (FHS).

The FHS is maintained by the Linux Foundation, and much like a lot of
the other standards we have talked about is a recommended standard so
that code written for one Linux distribution will be cross-compatibile
with another. Primarily, the FHS is a way of organizing user, program,
and system files in a tree-like hierarchy, which makes it easy for us to
install, uninstall, and find specific files.

# Important Directories

### '/' aka Root

Our tree starts from '/', the root. No matter what device a file is on,
it will be accessible from the root directory. Root is the highest level
of the hierarchy and everything falls underneath it. To access root, we
use the representation `/`. Right now, cd into root.

From there, run `ls` to see the available directories.

### Root Directories

Read through
\[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard\](this
link) and click through the files a bit to get an idea of what is going
on in each of the root directories.

If you do not have internet access, you can access information on the
FHS with \`\`\`man file-hierarchy\`\`.

This is a weird part of Linux as what we see today is the end result of
years and years of design tradeoffs, historical reasonings, and heated
debates. A few directories don't really make sense anymore, a few things
are brand new. All of this is critical in the "In Linux, everything is a
file" philosophy.

For your assignment, describe the following directories and what is
saved in them. If there is anything notable about the use of the
directory, or how the permissions are applied, please include that.

I expect you to have a large number of Pre-Questions for this
assignment, and it will take you a reasonably long time. Don't beat
yourself up too hard about this, but instead use it as a way to assess
your current understanding and fill in your gaps. If anything is
completely foreign to you, let me know in your feedback and in
\#feedback.

1.  `/`
2.  /root
3.  /boot
4.  /bin and /sbin
5.  /etc
6.  /home
7.  /lib
8.  /usr
9.  /var
10. /tmp and /var/tmp
11. /dev
12. /mnt and /media
13. /proc and /sys

Please respond in the appropriate format:

I know this is a longer assignment but it is very important.
