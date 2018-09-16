+++
title = "Let's talk about TDD"
date = 2018-09-16T15:50:28+02:00
draft = false
tags = ["Let's talk about", "TDD"]

+++

1. Red
2. Green
3. Refactor
4. Repeat

**Test Driven Development**, also known as "this would be so cool if green started with an R".

So this new (as in 1957) way of programming has been catching on lately, and I've had to clarify many points about what TDD is and isn't. I want to talk about some things related to *my* vision of TDD (which might not be yours, and that's ok).

# What does it mean?

Many people say they do TDD, and they do wildly different things from each other. I don't think there is "one way" to do TDD, but there are a few basics I think we need to consider to truly be able to name something TDD:

1. Tests before code
2. Quick cycles
3. Lazy implementation

## Tests before code

This is the one that at least 95% of people seem to agree on.
If you're not doing your tests, thinking about how your code will be used, *before* implementing whatever it is you're doing, you're not doing TDD (and if you're not even doing them afterwards, I would argue you're not even programming, you're just hoping it works).

## Quick cycles

The whole point of TDD is to Red-Green-Refactor quite quickly.

Ideally most iterations would be about a minute and there would be no poverty or hunger in the world, but in real life, you can usually expect most iterations to be 5 minutes and your alarm bells should start going off if you ever pass 15 minutes.

## Lazy implementation

Also known as YAGNI (You Aren't Gonna Need It).

This means only concern yourself with writing the code that you wrote the test for.
Many times we try to think too far ahead and end up creating excess code that is completely unnecessary and TDD is one way to avoid that.

# Let's talk about TDD

Now we've got the basics out of the way and I can talk about a few things that either come up or just plain irk me when discussing the subject.

## Wat be Unit?

People tend to say that you write Unit Tests when using TDD.
I absolutely despise the word *Unit* in this context.

Why? Take any three programmers, ask them what a Unit is in the context of Unit Testing and you will get *at least* seven different answers, which may or may not include:

1. A single method on a class
2. A pure function
3. A class
4. A single set of responsibilities
5. A single API entry point
6. The smallest logical unit of code
7. Anything requiring no imports to be run
8. Code that runs in under X milliseconds
9. ...

I would not have a problem with this if people weren't so crazy adamant about how every test should follow their definition of Unit.

So let's please just agree that the name is stupid and let's try to be less ambiguous and maybe call them something like Programmer-Oriented Tests or some other thing (I take suggestions)

## Test-Driven Refactoring

A lot of people think it's too late to start doing TDD when the big ball of mud is large enough.
However, in my experience, TDD is *the best tool ever* to "break the monolith" and start refactoring things to be sensible.

Just because you don't have tests doesn't mean you can't start making some and refactor as you go. It's usually less painful than the "stop everything and refactor" approach (which I've only seen be successful once and I'm still impressed it even worked).

## Tests after code

Some people prefer to do their tests after their code.
My reaction is usually "but why, though?"

Testing after the implementation is weird.
It's defining the problem once you already have a solution.
If you're going to take the time to write tests anyway, do them first and reap the benefits, right?

## Tooling

You don't need tooling to do TDD.
You just need `assert`.
And if you're language doesn't have `assert`...

    function assert(condition) {
        if (condition) raise Exception
    }

Boom. Assert.

# End?

So I guess this was just kind of a bunch of random disconnected thoughts dumped here with zero regard for drawing any conclusions, but I hope it will someday be helpful to someone to have this here.

Please feel free to open an issue at my [Github](https://github.com/kenan-rhoton/kenan-rhoton.github.io) if you think I should add or change anything!
