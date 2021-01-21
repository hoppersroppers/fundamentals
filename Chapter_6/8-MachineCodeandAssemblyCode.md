# Machine Code and Assembly Code
In order to be executed on a CPU, code must be written in a way that is understood by the CPU. This is called 'Machine Code' and consists of 1s and 0s. As a note, there are various families of CPU architectures which require different machine codes to operate properly. Humans don't like 1s and 0s as much as computers so we prefer to abstract ourselves away from the bits as far as possible. The first step of this is something called an "Assembler". You can generally think of an assembler as a piece of code written for a specific type of CPU that does a 1 for 1 exact translation of code into binary that can be executed.

I like this video: <https://www.youtube.com/watch?v=wA2oMRmbrfo>

Assemblers do a 1 for 1 translation, but what if we are looking for something that can optimize or simplify the work needed to be done by the programmer? In that case we would need something called a compiler. A compiler is a computer program that translates computer code written in one programming language (the source language) into another programming language (the target language). This allows the programmer to save huge amounts of time and spend more time doing and less time working.

Hey, read this about our namesake Grace Hopper and the first compiler: <https://history-computer.com/ModernComputer/Software/FirstCompiler.html>

Watch this: <https://www.youtube.com/watch?v=IhC7sdYe-Jg>

Some day, you will probably write a compiler so all of the things you just learned about makes more sense to you. Or you can not. I did it once. Didn't get as much out of it as people told me I would.

What we went over was just the absolute basics of computer hardware. I did not spend any time on Machine Code and Assembly, and you will get destroyed by it the first time you see it. My recommendation, avoid anything involving machine or assembly code until after you have spent some dedicated time on the subject. This means, don't try to jump into any Reverse Engineering problems, for now.