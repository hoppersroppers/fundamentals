# Make it Your Own!

For your first trick, we are going to modify your wallpaper entirely
from the command line.

This only works if you are in a Gnome-based desktop environment, which
you would have if you installed Ubuntu. I can't promise anything if you
are in another OS, so run this: 

``` default
echo $XDG_CURRENT_DESKTOP 
```

If it doesn't say Gnome, just skip this section, or for bonus points,
figure out how to change your wallpaper from the command line using
Google.

  

First we have to download an image, and then we will use the command to
make it our background.

``` default
$ wget -O ~/Downloads/wallpaper.jpg  "https://raw.githubusercontent.com/hoppersroppers/hoppersroppers.github.io/main/_layouts/constitution.jpg" 

$ gsettings set org.gnome.desktop.background picture-uri file:////tmp/wallpaper.jpg
```

Now your background image should be a picture of a ship! If it didn't
work, troubleshoot. If you're not on Ubuntu there is a very strong
chance that you have a different default Desktop (aka GUI) environment
on your OS and it doesn't use 'gsettings'. Google around to figure out
which Desktop environment you have and what you need to do to change
your background from the command line.

Alright, you don't need to keep it like that, go make it whatever
background you want!

## Assignment

``` default
Questions:
1. Using the 'man' command, describe what the command using wget and the -O flag did 
2. Using the 'man' command, describe what the command using gsettings did. 
If that didn't work, explain what you did to get it to work. 

Resources:
0. Man 
1. Google
```

Write up a few sentences for each of the questions. 
