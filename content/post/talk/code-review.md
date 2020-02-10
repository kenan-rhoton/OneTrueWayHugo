+++
title = "Let's talk about Code Reviews"
date = 2020-02-10T18:30:23+02:00
draft = false
tags = ["Let's talk about", "Code Reviews"]

+++

Also known as "just hit accept, I checked it already!".

The Code Review is a practice that dates back to ancient times when someone would finish writing some code (in this case the Hammurabi Code) and someone else would check to make sure they hadn't made any stupid mistakes.
So I guess you'll understand me when I find it surprising we still do it wrong.

What do I mean by wrong? Let's look at some common types of bad code reviews.

# "The code seems fine"

Meet Jake McJakeson. He's a relatively junior programmer with some experience here and there who's actually quite talented at the whole "writing words in some obtuse computer language until it works" thing we usually call software development. Jake finds a code review assigned to him, reads the code quite thoroughly and finds it to be correct. So he hits the "Accept" button and goes onto his next task finding that pesky bug.

The code then breaks horribly in production.

What went wrong? Well, multiple things, starting with the code obviously having some defect. But what mistake did Jake make? *He thought he was a computer*. What I mean by this is computers are pretty good at interpreting code and calculating outcomes. Humans? Not so much.

That code needed to come with tests. And Jake had to run those tests and check that the tests, *as well as the code*, made sense. So let's add those items to our list for a good code review:

1. The code must pass all tests
2. The code must have its own tests
3. The tests must be good

But that's not all that could be improved. Let's go meet someone else.

# "All green!"

Meet Sandra O'Sanderson. She's got much the experience with the doing of the programming. She's even into TDD! Yeah, she's top-notch programmer material. She finds a code review assigned to her and runs the tests herself before even reading anything. She finds they pass and, after a good hour spent reading through the intricacies of the tests and code, finds it all to be acceptable and correct, so she gives the green light!

The code then breaks horribly in production.

What went wrong this time? Sure, the tests were fine and covered most use-cases, but some of those cases weren't tested for. How did Sandra, an experienced developer, miss that? The answer is simple: the code was as unreadable as Twilight. If Sandra, instead of devoting time to try to understand the crazy mess of code that somehow worked had instead been like "Yo! Karl Karlson! This code's a mess. Make it not a mess or I ain't approving squat!" she would've been able to then devote her energy to the other problem: the tests didn't cover everything they needed to. So let's expand our list:

1. The code must pass all tests
2. The code must have its own tests
3. The tests must be good and cover all cases
4. The code (including the test code) must be readable

So there we go! We know how to make a code review! There's no way there are other problems that can

# "That's quite beautiful, son"

Meet Jack "Jackie" Jackson IV. This guy is a senior. Like the real deal kind of old guard. And the good kind of old guard, who did Agile before most of us were even born and who say crazy things like "Java is a modern language" or "I think we can improve on the COBOL unit tests". Jackie gets assigned a Code Review and returns it five minutes later asking for clarification for a specific function that has too high a ciclomatic complexity. Eventually, the code is a thing of beauty which Alan Turing would weep tears of joy for and Jackie gives it the thumbs up. And everything is fine! Nothing breaks, and Jackie continues on with his tickets and on with his life like a good senior software developer.

Two months later the code breaks horribly in production.

What went wrong? Like seriously? Surely I can't blame a two-month old code review for a recent bug, right? It was clearly Cassandra Cassidy's latest commit that broke everything! Jackie did nothing wrong! #freejackie2020. Well that beautiful code he let into production was part of a 21622-line file called `core.php` (don't you love such descriptive names?) where, despite most of the code being quite good, it was quite hard to do things like: find the right function/definition, check if some functionality already existed (unless you already knew the name), understand where you were even supposed to put the new code... So yeah, Cassandra goofed up, but Jackie, with all his experience, should've been like "Yo! This is a bad idea! Abort mission! We need to break this file down!". And so we get to our final list:

1. The code must pass all tests
2. The code must have its own tests
3. The tests must be good and cover all cases
4. The code (including the test code) must be readable
5. The code (including the test code) must be well-organized

So as we see, making a code review is

# "A job well done"

Meet Sir Edward Edwards, commonly known as "Sir", who has been knighted by Queen Elizabeth II for his excelency in code. He gets a code review assigned, checks it passes the tests, checks the test code, the readability and the organization and it is all deliciously perfect. He salutes his screen as he merges the commit to master.

The code then breaks horribly in production.

Now this is getting silly. I know. What could there possibly have been left for Sir (Mr. Sir to you, actually) to do? He did everything right! He even checked my blog to make sure he got everything right. Sadly, he missed this last crucial section where we come to the most obvious thing to do in a code review and which, surprisingly, few people actually do.

He never tried the code himself. If he had actually run the code in his machine, the code that perfectly passed all the tests, he would have immediately realized that the CSS was horribly mangled and the menus were overflowing from the screen, making the site suddenly impossible to navigate. He forgot to not just trust the process, but to trust his eyes. So this time we *really* are at the end. I promise. No takebacksies.

1. The code must pass all tests
2. The code must have its own tests
3. The tests must be good and cover all cases
4. The code (including the test code) must be readable
5. The code (including the test code) must be well-organized
6. The code must work when executed

# Final thoughts

This post may or may not be motivated by too many people asking me questions about code reviews alongside some masochists asking me to retake the blog. As always, I try to be thorough, but I still make mistakes! *Use responsibly*.

Please feel free to open an issue at my [Github](https://github.com/kenan-rhoton/kenan-rhoton.github.io) if you think I should add or change anything!
