# Basics of Networking

# <iframe allowfullscreen height="360" src="https://www.youtube.com/embed/F43P_yAcscE?wmode=opaque" width="640"></iframe>Networking is complicated and how it all works is saved for an entirely different course, but for now there are a few main tools you need to learn in order to take your first steps towards becoming a guru.

I am going to handwave a bunch of things, just trust me, what I'm
handwaving doesn't matter that much for now. This is all part of some
kind of plan.

## IP Addresses and Basic Networking

You might have heard the word IP address before, but we aren't going to
dive too deep into it yet. Just think of it as the way other computers
know who you are, and based off of a complicated routing system, how
computers in between you and whatever you are talking to knows how to
transport things back and forth. There will be plenty more on this in
the Networking Course which you are going to do next anyway, so don't
worry about how it works.

To find out your IP address, run the command "ip addr". This will print
out a list of things called interface and some other stuff, don't worry
too much. For now, focus on the IP addresses, the items in the form
127.0.0.1, 192.168.20.45, 182.16.10.100, 10.2.5.24 etc.... addresses in
that form are known as IPV4 addresses. (There's another format known as
IPV6 that looks like *2001:db8::8a2e:370:7334* but we aren't going to
worry about them right now)

You should only have a few of them, so look for your 127.0.01 address.
This is called your localhost, aka, your computer's local IP address. It
is completely internal, and all computers have a localhost at 127.0.0.1.
This means that you can't talk to someone else's localhost address and
it is non-routable.

You should have at least one more IP address listed, likely in the
format 10.x.x.x, 192.168.x.x, or 172.x.x.x. These address ranges are
known as "local" addresses. Long story short, there aren't enough IPV4
addresses. If you want to read more about this,
<a href="https://en.wikipedia.org/wiki/IPv4_address_exhaustion"
rel="noopener" target="_blank">the wikipedia article</a> is decent.

To get around the lack of IPV4 addresses, most private networks use
these local addresses for all the computers on it, so that they don't
need to own all the IP address space required for all of their computers
(what? people own IP addresses? Yeah it's super complicated, we're gonna
ignore that for now)

So when you see those local IPV4 addresses, what you are seeing is the
IPV4 address your network has assigned to you to use locally (and only
locally).

## Routing

How do we connect to the internet then? Well, there's some magic called
routing we aren't going to worry about too much for now, other than to
be confident that it works.

Let's trace our route to google.com to confirm that routing is working
properly. In linux, this uses the command `traceroute`. Windows uses
`tracert`.

``` default
$ traceroute google.com
```

You should see a nice fancy print out of all the servers you've hopped
across, starting with your gateway router and ending with the google.com
server. This family of commands is especially useful for troubleshooting
networking problems.

(For a fun hack, try `traceroute bad.horse`. Gotta love abusing
protocols to do cool things)

So what does google see you as when you make a request?

I recommend a quick trip to a website to find that out!
<a href="https://nordvpn.com/what-is-my-ip/" rel="noopener"
target="_blank">Click here to find your public IP</a>.

As you can see, your public IP is completely different than what your
local IP is when you run `ip addr`.

The reason for that is something called NAT, or Network Address
Translation which is a method of mapping one IP address to another by
modifying packets while they are in transit. It's hella complicated how
it works, but what matters to us, the end users, is that our local
address is stored by some NAT server which ensures that any responses to
traffic from us that leaves our network, comes back to our locally
assigned IP. On the other hand, nobody should be able to connect into a
box behind NAT because they will not know the local IP address and
either way, a local address shouldn't be routed across the internet. So
just remember for now, NAT allows connections out and responses back,
but does not allow connections in. (Just smile and wave, nobody
understands NAT, but we'll go over it a bit more in the Networking
Course).

How does routing work? How do the packets actually get from Point A to
Point B? Patience my friend. Later in the course in the web section we
will talk about it.

## VM Networking

So how does this all tie back into practical application? Well your
Virtualization Software will have an option to switch your VM between a
NAT'd IP address and a Bridged IP address.

I don't spend much time on Windows in this course, but run the command
`ipconfig` in your Windows CMD prompt to get your host computer's IP
address.

Bridged IP addresses are IP addresses assigned by your local router,
which will be NAT'd by the router when you try to connect out. NAT'd IP
addresses are IP addresses assigned by your virtualization software,
which puts that box behind a NAT. This means that if you are NAT'd,
another local computer will not be able to connect to you, but if you
are Bridged, your IP address will be routable. You're still both behind
a router NAT, but it's the same NAT so you'll share the same IP address
prefix.

Depending on your Virtualization Software, switch between the different
networking modes and see how your IP address (and routing) changes. Run
the `ip addr` command to check. If you are having trouble switching,
assume that it is because Windows Hyper-V is doing bad things (even if
you aren't using it). It's possible to fix Hyper-V issues by "disable
network interfaces hyper-v" (there's your search term), but it's mostly
a pain that pops up every once in a while.

-   <a
    href="https://www.vmware.com/support/ws45/doc/network_configure_ws.html"
    rel="noopener" target="_blank">VMWare</a>
-   <a
    href="https://wiki.dave.eu/index.php/VirtualBox_Network_Configuration"
    rel="noopener" target="_blank">Virtual Box</a>
-   <a
    href="https://docs.microsoft.com/en-us/archive/blogs/virtual_pc_guy/using-hyper-v-with-a-wireless-network-adapter"
    rel="noopener" target="_blank">Hyper V</a>
    -   Don't try to do the HyperV one, it's a nightmare. Just install
        VMWare.

Over the next few sections, think about how changes in your local
address will effect routing.

## Netcat

Netcat is known as the "Swiss Army Knife" of networking tools. Whatever
you want to do, you can probably do it with netcat. It comes
pre-installed on most Linux machines, which makes it a common
troubleshooting tool. While there are many features, the most common use
is that you can use it to send and receive arbitrary data across a
network. The way we send data across a network is with things named
"protocols". Netcat speaks the TCP and UDP protocols, but that doesn't
matter all that much right now. Protocols run everything online, but we
are going to save learning how they work for later. 

Using pipes and redirectors that we learned about in the last lesson, we
can choose the input that is sent via the network, as well as what we do
with the data once we receive them. On the command line we can use `nc`
as a short name for the netcat program.

``` default
$ echo 'Hello World' | nc 127.0.0.1 1337
```

When we run this first commnd, we take the STDOUT of echo and pipe it as
the STDIN of netcat. The first argument for netcat is the IP address we
want to send it to, and the second number is the port we want to send it
to. Netcat will then send 'Hello World' off to the correct location.
Networking is hard, but we will skip a lot of the hard stuff for now. At
this time, just know that most computers have an IP address and have
thousands of ports. If two computers want to pass data over a network,
they have to know the correct IP address and port to send data to. 

In this case, we are using netcat to send 'Hello World' to IP address
127.0.0.1 to port 1337. IP address 127.0.0.1 is often known as
localhost, and is our current computer. You can also write that command
as:

``` default
$ echo 'Hello World' | nc localhost 1337
```

If you noticed, nothing happened, which is kind of expected. How can we
see if data was sent without setting up something to listen? Now we get
to see what netcat can really do! Open up a new terminal and set up a
listener on localhost port 1337 with this command. (As a note, there are
multiple versions of netcat, all named the same thing. Sometime they
behave differently and have slightly different flags. The following
command should work for all versions of netcat.)

``` default
$ nc -lp 1337
```

Now you have set up a listener, go and run the first command again from
your other terminal to send 'Hello World'.

Look at that! You have NETWORKED!!!!! To stop listening, press ctrl-c.
That generally closes out or "interrupts" most processes in the
terminal.

Let's talk about what just happened. First, you set up a "server", the
listener. Then you had the "client" send data to the listener. This is
about the most basic client-server setup you can get, but the principles
remain generally the same all the way up to the complexity of web pages.

## Send a File

For more fun, we can even send files around using redirectors because of
how well Linux handles streams.

First modify your listener to output to a file using '\>'. Then, use
`cat` to read an existing file into a stream and then use '\|' to pass
it into netcat.

Now you should have transported the file into the new location where
your listener was pointing!

Alright, so that wasn't magic, though it is pretty cool. In the future
we will look at this traffic as it moves around the network so you can
get a better understanding. For now, just know there are rules that
govern exactly how it works and soon you will fully understand it.

## Rainbow Connection

To do something really cool, make a clone of your current virtual
machine and run two VMs side by side at once (You'll need at least 4GB
of RAM). Once you have them both spun up, run "ip addr" to get each
box's local IP address. Get the networking going properly that you are
able to connect between the two boxes using those netcat tricks. If you
are with a friend, get their IP and just try to connect to each other's
box, no clones needed! (As a useful hint, you need to be on the same
local network to be able to "route" to eachother's IP addresses. If you
are both behind NAT or host-only it won't work, so I recommend you
switch your VM Networking to Bridged and make sure you are on the same
WIFI network.

You might need some Google but it is pretty cool.

If you don't want to do this, or your computer doesn't have the space,
don't do it. Just make sure you have an idea of what would be going on.

## curl

There are plenty of tools (like `wget` which we used earlier in the
course) to download a file from the terminal, but I prefer to teach curl
as it is able to support the most protocols (and can upload too if you
need it). Curl is super useful to quickly grab resources if you have the
URL. There are a ton of flags to let you do whatever you need, but don't
worry, there are also plenty of great cheat sheets like
<a href="https://devhints.io/curl" rel="noopener" target="_blank">this
one</a>

If you do not have curl installed, you will have to install it using
apt-get. I think you can do that by yourself now.

Most of the time, this is all the command you need to download a file.

``` default
$ curl  -o image.png https://raw.githubusercontent.com/hoppersroppers/hoppersroppers.github.io/master/_layouts/compass.png
```

If you don't have curl on a system, the easiest way to download a file
is `wget`. There are a lot fewer features, but that doesn't mean it
won't work. Note the capital O vice lowercase o.

``` default
$ wget  -O image.png https://raw.githubusercontent.com/hoppersroppers/hoppersroppers.github.io/master/_layouts/compass.png
```

## See What Is Doing What

For something I am going to hand-wave, but at least is very interesting,
I'll introduce two commands that show you what is making connections on
your computer and tell you basically nothing else about them. They are
cool but a bit overkill for what we are doing right now.

Before we run them, set up a nc listener and connect to it. After you
run the commands, go look for the nc processes... You should be able to
find them!

``` default
$ netstat --inet -ap
```

``` default
$ lsof -i
```

For a pro-tip, anytime you want to look like a hacker, run these
commands and you'll have a very cool looking display up.

## Telnet

Telnet is an old fashioned protocol that usually provides nice and easy
shell access to anyone running a telnet server, which is often
unauthenticated. It's a hacker's dream!

Too bad you don't see many of them these days, but they are common in
CTFs, and on critical infrastructure (jokes?).

Here's a fun telnet demo to show what it is capable of:

``` default
$ telnet towel.blinkenlights.nl
```

Hackers gonna hack. And bored people... well they're gonna bored people.

## SSH

Another very important tool is Secure SHell or SSH. They are basically
the secure successor to Telnet for providing remote shells.

We won't go into the networking specifics of this yet, but SSH is a
networking protocol that allows encrypted access to remote computers.
How this works in effect is a remote computer, the SSH server, will
listen for an incoming connection. The local computer, which is the
client we are trying to SSH from, sends a request via the SSH protocol
to log in to the SSH server. If the password supplied is correct, the
server will then create a shell on the remote computer and then pass
back the stream from that shell to the client. From there, the client
who just logged in via SSH is able to have access to the remote computer
in an encrypted manner.

I hand waved a ton of complexity there, but it doesn't matter yet. We'll
spend some more time on this in the networking course, but you honestly
don't need to know the specifics, I certainly don't.

To SSH, you can either use a password or a key. Most of the time you
will have a password, and that is what we will focus on in this course.
The networking course will have more info on keys and SSH.

To use ssh, simply run the command: `ssh username@domain.com`. There are
plenty more options, but this one will get you through 90% of use cases.

Now, let's move on to the next section and use SSH.

  
