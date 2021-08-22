# Python Hello World
This might require some googling..... don't worry, that is how everyone does it. You find something you need to do, and google how to do it. Then you forget how to do it, and you go and google it again the next time you do it. The next bit will help you set up your python environment on Linux. Setting up environments is very time-consuming, no matter what it is, but you will have to do this for basically every language, and every version of each language, so you will have to get good at it.

# Linux

Ensure the most up to date version of Python is installed on your Linux box. Check this by running the command ```python``` from the command line. 

If it responds with Python2 or the program is not installed, install a modern Python version with <https://docs.python.org/3/using/unix.html#on-linux>

When you run ```python``` from the command line it brings up something called an interpreter. The Python interpreter is neat because you can use it to run programs one at a time. 

With the interpreter open, do some basic math. 

```
a = 2 
b = 3
c = a + b
print(c)
```

That should have printed c, which would have displayed as 5.

You can also print text from the interpreter. A program that prints "Hello World!" to the screen is the classic first thing most tutorials teach. Far be it from me to break with tradition, so here goes!

``` 
print("Hello World")
```

Make sure to have the quotes around the words that you printed. Don't worry about what is happening right now, this is just to show what is possible. To close out the interpreter, type ```exit()```. 

# Hello World

We used the interpreter, but you can only do very basic programs from the interpreter, so usually you run python programs as their own files. 


Python makes this incredibly easy in comparison to many other languages. 

Here is the code:

``` 
print("Hello World!")
``` 

You might notice that as the same thing that the interpreter took as input. Save it as "helloworld.py".  ".py" is the python file extension. It is just a text file, but the ".py" tells the OS what to do with the file if you try to execute it. 

Then, from the terminal, run that file you just created with: 
```
$ python helloworld.py
```

Congratulations! Now you know how to program in Python! Sure, there are a few steps between here and writing complicated programs, but... we'll get you there during this course!

# Assignments 

1. Submit the code for a python program which adds 1,2,5, and 6 together, then prints the results to the screen. Use comments to explain what is happening. There are multiple ways to do this. 
2. What is a path in regards to Python. You might have to google around to understand it. Hint: If you mess this up, things get interesting.
