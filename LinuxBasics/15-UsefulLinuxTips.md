# Useful Linux Tips

<iframe allowfullscreen class="fr-draggable" height="360" src="https://www.youtube.com/embed/OcXmPsvxkRA?wmode=opaque" width="640"></iframe>

  

There are a ton of commands out there to make you more efficient on the
command line, but let's highlight some of the best right now!

### Tab Autocomplete

I mentioned it before, but I need to mention it again. Hit the tab key
to autocomplete words/paths/anything and save yourself time. Double tap
it to get a listing of possible options.

### cd

We all know `cd`, but did you know about `cd ~` which takes you to your
home directory, and `cd -` which takes you back to the directory prior.

Do some morphing around your filesystem and use `cd` tricks to navigate.
Check out what happens if you just type `cd` with no arguments.

## History

You can look at your most recent command history using the command
`history`, and combining that with `grep` you can pipe the two together
to search your most recent commands. But even easier than that is typing
ctrl-r, which kicks off a search in your history for you.

## Line Navigation

If you have a super long command and don't want to arrow through the
whole thing, you can use "home" and "end" keys on your keyboard. Even
more efficiently than that though, you can ctrl-a and ctrl-e to zoom to
the front and back.

## Reuse Commands

Ran a command and forgot to use sudo? Use the "!!" operator to run the
same command again, and `sudo !!`. If you want to run the most recent of
a certain command, use the single "!" operator and the command name,
such as `!ls`, which will run the most recently executed `ls` command.
Much easier than pressing the up arrow until you find what you are
looking for.

## Kill Processes

If something is running, ctrl-c should do the trick if you are in the
same window as it. If not, ctrl-x is a great standby. You'll learn more
about killing processes in the next section.

## New Terminal

In Ubuntu, ctrl-shift-t should pop open a new terminal for you to hack
in. If you are already in a terminal, it should pop up a new tab. To
switch between these, ctrl-pagedown or ctrl-pageup.

To open a new window, ctrl-shift-n should open a new terminal window.

With that said, these are very OS specific and might not be the same for
you. If that is the case, google for your operating system terminal
keyboard shortcuts.

Of course, there are so many of these and you can always add more, but
this is enough to get the most bang for your (free) buck.
