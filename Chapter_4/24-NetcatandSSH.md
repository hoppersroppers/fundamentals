# Basics of Networking

Networking is complicated and how it all works is saved for an entirely different course, but for now there are two main tools you need to learn in order to take your first steps towards becoming a guru.

## Netcat
Netcat is known as the "Swiss Army Knife" of networking tools. Whatever you want to do, you can probably do it with netcat. It comes pre-installed on most Linux machines, which makes it a common troubleshooting tool. While there are many features, the most common use is that you can use it to send and receive arbitrary data across a network. The way we send data across a network is with things named "protocols". Netcat speaks the TCP and UDP protocols, but that doesn't matter all that much right now. Protocols run everything online, but we are going to save learning how they work for later.

Using pipes and redirectors that we learned about in the last lesson, we can choose the input that is sent via the network, as well as what we do with the data once we receive them. On the command line we can use ```nc``` as a short name for the netcat program.

```
$ echo 'Hello World' | nc 127.0.0.1 1337
```
When we run this first commnd, we take the STDOUT of echo and pipe it as the STDIN of netcat. The first argument for netcat is the IP address we want to send it to, and the second number is the port we want to send it to. Netcat will then send 'Hello World' off to the correct location. Networking is hard, but we will skip a lot of the hard stuff for now. At this time, just know that most computers have an IP address and have thousands of ports. If two computers want to pass data over a network, they have to know the correct IP address and port to send data to.

In this case, we are using netcat to send 'Hello World' to IP address 127.0.0.1 to port 1337. IP address 127.0.0.1 is often known as localhost, and is our current computer. You can also write that command as:

```
$ echo 'Hello World' | nc localhost 1337
```

If you noticed, nothing happened, which is kind of expected. How can we see if data was sent without setting up something to listen? Now we get to see what netcat can really do! Open up a new terminal and set up a listener on localhost port 1337 with this command.

```
$ nc -l 1337
```

Now you have set up a listener, go and run the first command again from your other terminal to send 'Hello World'.

Look at that! You have NETWORKED!!!!! To stop listening, press ctrl-c. That generally closes out or "interrupts" most processes in the terminal.

Let's talk about what just happened. First, you set up a "server", the listener. Then you had the "client" send data to the listener. This is about the most basic client-server setup you can get, but the principles remain generally the same all the way up to the complexity of web pages.

## Send a File

For more fun, we can even send files around using redirectors because of how well Linux handles streams.

First modify your listener to output to a file using '>'.
Then, use ```cat``` to read an existing file into a stream and then use '|' to pass it into netcat.

Now you should have transported the file into the new location where your listener was pointing!

Alright, so that wasn't magic, though it is pretty cool. In the future we will look at this traffic as it moves around the network so you can get a better understanding. For now, just know there are rules that govern exactly how it works and soon you will fully understand it.

## curl

There are plenty of tools (like ```wget``` which we used earlier in the course) to download a file from the terminal, but I prefer to teach curl as it is able to support the most protocols (and can upload too if you need it). Curl is super useful to quickly grab resources if you have the URL. There are a ton of flags to let you do whatever you need, but don't worry, there are also plenty of great cheat sheets like [this one](https://devhints.io/curl)

If you do not have curl installed, you will have to install it using apt-get. I think you can do that by yourself now.

Most of the time, this is all the command you need to download a file.
```
curl  -o image.jpg http://www.example.com/abcdefg123.jpg
```




## SSH

Another very important tool is Secure SHell or SSH. We won't go into the networking specifics of this yet, but SSH is a networking protocol that allows encrypted access to remote computers. How this works in effect is a remote computer, the SSH server, will listen for an incoming connection. The local computer, which is the client we are trying to SSH from, sends a request via the SSH protocol to log in to the SSH server. If the password supplied is correct, the server will then create a shell on the remote computer and then pass back the stream from that shell to the client. From there, the client who just logged in via SSH is able to have access to the remote computer in an encrypted manner.

I hand waved a ton of complexity there, but it doesn't matter yet. We'll spend some more time on this in the networking course.

For now, let's move on to the next section and use SSH.
