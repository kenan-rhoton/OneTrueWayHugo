+++
date = "2017-05-27T18:18:05+02:00"
draft = false
title = "When Should I Use Python?"
tags = ["When Should I Use","Python"]

+++

[Python](https://python.org) is a beautiful language. It really drives home the message that simplicity can be powerful.

It's also incredibly deep, and it is probably the oldest designed language from the tribe of "We can make programming a creative experience."

It also introduced me to the amazing concept of Test Driven Development, due to how much emphasis is made on it (and how much tooling there is) in the Python world, especially thanks to Django.

But let's get down to business...

## What is Python

Python is a programming language that really treats programming like an art.

With an emphasis on beautiful, simple, sparse, readable and practical code, it, along with [Go](https://github.com/golang/go), are the two languages in which I truly believe I could just give some random (but well-written) code to someone with no idea whatsoever of the language and it would be understood.

It makes a number of surprising choices that actually make a lot of sense (Indentation as Syntax? What!).
It has a very mature and well thought out set of functionalities.

It is a joy to program in Python, really.

I think that, as a developer, there are some specific things to understand about Python.

1. The Syntax is simple, but powerful
2. Readability gives you Power and demands Responsibility
3. Pip is your friend
4. Virtualenv is your building block
5. Read the docs, you will understand them easily
6. Test all the things

### The Python Syntax

    import re

    with open('somefile.txt', 'r') as f:
        for line in sorted(f):
            if re.search("potato", line):
                print(line, end='')

Look at this code. Just *look* at it.

Even if you've never heard of Python it's pretty simple to understand that it:

1. Imports the "re" module
2. Opens a file as **f**
3. Iterates over the sorted lines
4. Prints any line containing "potato"

It all feels very natural and at the same time it's not at all limiting.
You can both be very precise and very readable with Python's syntax.

Also, although this is more a matter of opinion, I think indentation as part of the syntax is genius: everyone indents their code anyway. And for the whole "tabs vs spaces" arguments, you just need to agree on a code formatter and be done with it.

### Readability: Power and Responsibility

But with Great Readability comes Great Responsibility. And that is to actually use the readability.

Consider the following "refactor" of the above code:

    from re import search
    f = open('somefile.txt', 'r')
    lines = f.readlines().sort()
    for l in lines:
        if search("potato", l): print(l,end='')

It may not look much worse, but you do have to pay more attention to the code to know what its doing... Also it has a bug, it's missing a call to `f.close()` which you're quite likely to miss.

The point is, that if you don't devote a little time to writing good code, you're missing out on one of the main advantages of Python.
Which makes me sad.

### Pip, the Package Manager

Python comes with a very important tool alongside: `pip`.

pip stands for "Packages in Python". Actually I just made that up. But it should stand for that, because that is what it does.

It functions much like every single other package manager, so we won't really spend much time on it.

Instead, let's talk about...

### Virtualenv

Before there was Docker, before there were things like Ruby's Bundler... there was the annoying problem of managing your dependencies.

