# Computers are Deterministic

<iframe allowfullscreen class="fr-draggable" height="360" src="https://www.youtube.com/embed/svCsYWE7bRM?wmode=opaque" width="640"></iframe>

  

All that I want you to take away from the next few sections is that
computers are, by definition not random, and they are not magic.

There are some very powerful applications of physics, hidden under
pieces of engineering, which themselves are hidden under layers and
layers of computer science, but there is no magic. We do not need to
understand physics to understand the software. What we do need to
understand is that computers are based on the laws of physics, and as a
result, the hardware is meant to be deterministic. ***Deterministic
means that given the same inputs, there should be the same outputs.***

To understand this, we work from the ground up. If electrons follow the
laws of physics every time (which they should), the hardware will work
the same every time. (Basically, the only exceptions to this are cosmic
rays and crazy hardware faults). If the hardware works the same way
every time, the software on top will run the same way every time. If you
ensure that your inputs remain the same, your output will be the same.
This means that we can take the same data, same configuration, and run
test cases, and everything will come out the same way every time. To put
it simply, there is an expected result and anything deviating from that
is correctable.

## Randomness

Software and hardware can be made non-deterministic by introducing
randomness. Randomness is an entire field of Computer Science based
around the problem of providing a random number to software. By adding a
random number generator, any code that runs after or on top of that
non-deterministic process will be similarly non-deterministic. A common
topic in Computer Science is the difference between true random and
pseudo-random number generators. The most common of the two is
pseudo-random number generators (PRNGs), which use software and a "seed"
to generate a random number. Seeds are fairly easy to predict, which
means that because the PRNG is deterministic if we can predict the
inputs we can predict the outputs. For nearly all applications, this is
good enough, but for some higher-stakes applications, especially
cryptography, we don't want there to be any chance someone can predict
our seed.

For those higher stakes scenarios, sometimes a true random number
generator is required. These TRNGs use something like radioactivity,
atmospheric noise, or a video of a bunch of lava lamps to create a truly
random seed as input. These TRNGs are considered non-deterministic,
because it is basically impossible to ever provide the same input and
get the same output ever again so they are considered safe to use.
Another form of TRNGs is a computer chip known as a Hardware RNG, which,
develops an input that is, based on known laws of physics, impossible to
predict. This makes the output perfectly unpredictable and can be
trusted to be truly random.

Overall, randomness is something we control because we choose to put it
into our software or hardware. Once we introduce randomness, we make our
programs harder to control and troubleshoot. Don't worry too much about
randomness, you very rarely need to do anything with it, which means
that you can rely on your computers being deterministic. Leave
randomness to the Computer Science PHDs and get on with the rest of your
life.

## Why this Matters

This idea of computers being deterministic is very powerful. It means
that computers are not magic. It means that because they do the same
thing every time, we should be able to troubleshoot any problems when
they occur by running the process again and seeing where the error
occurs. If we are on the same hardware, with the same OS, we can expect
the software to run the exact same way. We find where the error
(randomness) occurs, correct it, and now the process will run normally.
This idea of determinism is critical to seeing computers as something
that can be tamed, controlled, and understood. ***Computers want to
work.***

We don't need to understand the physics or the hardware, we just need to
know it is a constant. It has been abstracted away. We need to
understand the OS, and how our interactions with the OS modify it, but
we don't need to understand any deeper than that unless we want to.
