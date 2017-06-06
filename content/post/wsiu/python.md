+++
date = "2017-05-27T18:18:05+02:00"
draft = false
title = "When Should I Use Python?"
tags = ["When Should I Use","Python"]

+++

**DISCLAIMER**: *I don't claim to be an expert on this language, so I may have made mistakes. If there is anything you would say differently or anything that is just plain wrong, please open an issue on [Github](https://github.com/kenan-rhoton/OneTrueWayHugo)*

[Python](https://python.org) is a beautiful language.

Every language does have some kind of beauty to it (except for perhaps JavaScript), but Python really drives home the message that simplicity can be powerful.

It's also incredibly deep, and it is probably the oldest designed language from the tribe of "We can make programming a creative experience."

Python is also a very flexible language, which uses dynamic typing to a great effect and allows you to mix programming paradigms in a natural way.

And it introduced me to the amazing concept of Test Driven Development, due to how much emphasis is made on it (and how much tooling there is) in the Python world, especially thanks to Django.

But let's get down to business...

## What is Python

Python is a programming language that really treats programming like an art.

With an emphasis on beautiful, simple, sparse, readable and practical code, it, along with [Go](https://github.com/golang/go), are the two languages in which I truly believe I could just give some random (but well-written) code to someone with no idea whatsoever of the language and it would be understood.

It makes a number of surprising choices that actually make a lot of sense (Indentation as Syntax? What!).
It has a very mature and well thought out set of functionalities.

It is a joy to program in Python, really.

I think that, as a developer, there are some specific things to understand about Python.

1. The Syntax is simple and very readable
2. You have the power to do anything
3. External libraries for the rest
4. You will develop *fast*
5. Great documentation
6. It will be fun
7. Objective and Functional

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

### Python Power!

This would be an amazing name for a new Anime about Mutant Robosnakes.

But back to programming, Python is one of the languages with the most extensive and robust standard libraries that I know of.

In fact, the typical Python app doesn't have that many external dependencies other than whatever the framework you're using requires.

Everything from advanced math to crypto to compression to emailing to files and persistence (even sqlite3!) is baked into the standard library for you to import.

Frankly, the main reason for external dependencies is mostly "I could do that, but since someone else already did it I may as well use it".

It really is amazing just how *easy* it is to build a complex system in Python.

Also, a very big thing I find in Python is that it is easy to implement both Object Oriented and Functional solutions, with a versatility that is hard to replicate in other languages ([Ruby](https://www.ruby-lang.org) tries, though)

### External libraries

Python is a very mature language.

This means that there are libraries for pretty much anything you can think of.

UI? [Library](https://docs.python.org/3.6/library/tkinter.html). Web Framework? [Library](https://www.djangoproject.com/). Machine Learning? [Library](https://github.com/tensorflow/tensorflow). YouTube video downloader? [Library](https://pypi.python.org/pypi/youtube_dl/2017.5.29). ASCII Cats? I don't know why but there's a [Library](https://pypi.python.org/pypi/cats/0.2.0) for that too.

So this means it's actually very hard to come upt with a project idea where you will truly be "on your own" in Python, which is a great thing.

### Fast development

Developing in Python is *fast*.

It is amazing just how intuitive, expressive yet powerful the language can be, and the amount of content in the standard library and external ones helps to not have to reinvent the wheel and focus on the problem.

I also think its readability comes again with a lot of strength, as it is SO much easier to collaborate when you can easily understand what others have done.

This, coupled with **very** smart decisions when it comes to how things are implemented, makes for a very natural development flow that produces results much quicker than many other languages.

### The docs

The documentation is *amazing*.

Part of this really comes with being a mature language, but seriously, both the [Standard Library](https://docs.python.org/3/library/) and everything else is very extensively documented.

Really, I think at this point, pretty much every single doubt you could possibly have with the language is either documented somewhere or is answered on [StackOverflow](https://stackoverflow.com/)

### Fun, Fun, Fun!

Python programming is fun!

Ok, this is completely subjective, I confess, but I've heard it from multiple people (which has next to zero statistical value): Python is *fun*.

I think that the main reason for this is that it is so fast to go from **zero** to **Prototype One** that it simply *feels satisfying*.

And really, a happy developer is a better developer.

### Objective and Functional

The final aspect I want to touch on is how easy it is to use whatever programming paradigm you want to in Python.

Are you a Brave Clojurist who thinks only in pure functions? Python can do it. Do you need to create a Class with all sorts of overloading shenanigans? Python can do it.

This flexibility is part of what makes Python great: you are free to code in the **best way you can**.

## What does Python suck at?

So, we have a robust, versatile, easy, practical language. Where's the catch?

Like every other language, Python is not the perfect solution to every single problem.
And in fact it has some serious caveats as well as some minor deficiencies.

To be concise, we'll name the most prominent.

1. Not the fastest car in the race
2. Wait, there's Python 2 and 3?
3. \_\_init\_\_ and other fun things
4. Interpreted

### Speed of a camel

So Python is not the fastest language ever.
It's really more like "trying not to be last" in that regard.

Thankfully, that doesn't mean it's *terribly* slow, but clearly if you need to develop some very time-critical software, you should look elsewhere.

Like a camel though, it's stable and lasts long, so it's very decent for things like Web Server Backends, where really, the net latency renders Python's response time irrelevant.

But you won't be developing the next Real-Time Physics Engine for a AAA game in Python anytime soon...

### Python 2 vs Python 3

This surprisingly is still a problem, even thought you'd think that it'd be clear that people should just use Python 3 because the number is bigger (No one is using Java 5 anymore, right? Right?).

Python 3 was released in 2008, so the excuse of "X library is only in Python 2" is increasingly becoming less credible. I mean, there's a 99% chance that an equivalent Library exists for Python 3 and you're just lazy.

### Those weird underscores

Why exactly is the function to auto-convert a class to a string called "\_\_str\_\_"?. Why does prepending a variable with double underscore have a special meaning in a class? For that matter, why do I need to create an empty \_\_init\_\_.py file to make my project into a package.

These and other mysterious questions have been very annoying to people who, sure, found the answer to whatever they were looking for quite quickly upon searching, and then groaned loudly.

Because let's be honest, that's not the most intuitive and readable thing...

### Python is interpreted

This one is both a blessing and a curse.

A blessing because it means Python can run on any platform that has an interpreter implemented for it with next to no modification.

A curse because it not only makes the language slower (as discussed) due to its overhead, but it *requires* your users to have python installed. Which sucks.

This is probably why Python has been mostly used on things that are hidden from the standard user (servers or advanced user apps).

## So... When Should I Use Python?

Yes, Python is hard to live without.

Obviously the first thing to consider is if your project has high execution speed requirements, which is the first aspect that Python flunks.

Secondly, it's a language that just doesn't reach a true low level in any case, so for some "necessarily-low-level" things (such as drivers) you can't really consider it.

However, it is a *great* language for any team projects because of its readability. And because it is very robust, it's a great choice for companies. I mean, it's one of Google's official languages for development. That says something.

And its development speed is also a great plus for any project that needs to deliver things *yesterday*.

So Python is your rock. You can't really go wrong with choosing Python.

Just remember the Camel analogy: it's not very fast, but it will get you far.
