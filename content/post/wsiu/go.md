+++
date = "2017-05-19T16:41:02+02:00"
draft = false
title = "When Should I Use Go?"
tags = ["When Should I Use","Go"]

+++

**DISCLAIMER**: *I don't claim to be an expert on this language, so I may have made mistakes. If there is anything you would say differently or anything that is just plain wrong, please open an issue on [Github](https://github.com/kenan-rhoton/kenan-rhoton.github.io)*

[Go](https://github.com/golang/go) is a language that many people (yet not enough) are talking about.

Yes, it has the interesting origin of basically being designed by Google to solve Google's problems.
Yes, it looks at first glance like C with some random syntax changes.
And yes, why do you need to learn a new language to do the things you already know how to do?

But every language has its place, and today we're going to look at this beautiful construct (all languages are beautiful, really, except JavaScript) and try to find the answer to the question of *When to Use Go*.

And it all starts with another question:

## What is Go?

Go is a compiled language that strongly inherits from Alef and C.
However, it makes a special emphasis in some very interesting aspects:

- Simplicity
- Fast compilation
- Package management
- Channel-based concurrency
- Statically link everything
- Code Clarity

### Simplicity

The first thing to understand about Go is that it is stupidly easy to learn.
Anyone with any programming experience can learn it at a competent level in under a week.

This is in great part to the amazing amount of emphasis the Golang team have put on a clear language.

For example, here is an excerpt from a random repo I've been contributing to:

      func InvertColorMap() {
	    re := regexp.MustCompile(".*.fg")
	    for k, _ := range ColorMap {
		    if re.FindAllString(k, 1) != nil {
			    ColorMap[k] = ui.ColorBlack
		    }
	    }
	    ColorMap["par.text.hi"] = ui.ColorWhite
      }

It doesn't really take a rocket scientist to realize that this code simply does:

- Declare a function InvertColorMap with no arguments that does the following:
    1. Make a regexp for things ending in ".fg"
    2. Iterate the keys of a **ColorMap** thing.
    3. Find All Strings that match the **Regex** in the Key and if not nil, set that **ColorMap** key to ui.ColorBlack
    4. Finally, set the specific key of "par.text.hi" in **ColorMap** to White


Congratulations, you apparently already know Golang.

### Fast Compilation

Golang compiles *fast*. And I don't mean the "Just one cup of coffe" kind of fast. I mean "Are you sure I used the right build command?" fast.

As an example I timed the compilation of [Revel](https://github.com/revel/revel), one of the main Web Frameworks for Go (which is awesome, by the way) and the compilation took less than a second (specifically 0.879s of real time).

Granted, it's not the hugest app I could find, but it's a good representation I feel of a *useful app*.

As a bigger example, I also compiled the go compiler and its tools, and it took just 8m 20.068s, and about 40% of that was running the tests.

So if you care for fast compilation times, Go has your back, bro.

### Package Management

Go has taken the trend started by Python's `pip` and Ruby's `gem`, and integrated the package management system into the standard toolchain in the form of `go get`.

This is, IMO a fantastic thing, as there is a standard way of organizing your dependencies. However, `go get` is not without its caveats:

- `go get` kinda forces you into a monorepo, where your code is always located in `$GOPATH/src/github.com/kenan-rhoton/foo-project` or similar.
- It encourages a philisophy of always using the latest version of dependencies, which I find a good thing, but most people dont. You can opt out of that by vendoring the dependencies, but it's kinda ugly.

Some solutions have appeared that target these problems, chief among them is [Glide](https://github.com/Masterminds/glide), which essentially makes vendoring easy.

In most cases, though, this means that the only step to build a project is `go get -u github.com/user/repo`, which will automatically fetch the project and its dependencies, build it and install its binary (if any) into $GOPATH/bin.

**Update!**

Go is now introducing [Go Modules](https://github.com/golang/go/wiki/Modules) so it seems that there will be no true pain points left in this area (I even think they've surpassed every other package management tool for any language except perhaps Rust's Cargo).

### Channel-Based Concurrency

Here we can see a big part of its Alef influence: channels.

The "Go way" of doing concurrency is to simply launch a "goroutine" and communicate with it through blocking channels.

A quick example, since Go tends to be easier to understand by actually looking at code:

    import (
        "fmt"
    )

    func main() {
        c := make(chan string)

        go func(i chan string) {
            i <- "Hello, World!"
        }(c)

        fmt.Println(<-c)
    }

That is a complete Hello World program with concurrency.

Another cool feature in golang is that, although reading and writing to a channel is, in general, blocking, one can do a nonblocking read using the `select` construct:

    select {
        case res := <-i:
            fmt.Println(res)
        default:
            fmt.Println("Received nothing yet!")
    }

### Statically link everything

This is a funny one. I've heard two kinds of arguments:

1. Statically linking is a vestige of the 80s, dynamically link everything!
2. Statically linking is faster, clearer, cleaner and makes things not randomly break.

I'm in favor of the second one, so this section is a Go advantage in my mind, but feel free to disagree! (You can always open an issue at [github](https://github.com/kenan-rhoton/kenan-rhoton.github.io))

So Go compiles into a completely self-contained executable 100% of the time.
No worries about external things breaking it.
That has got to be good.

### Code Clarity

This is one of my favorite things: Go includes tools such as `gofmt` and `go vet` which define the code style and best practices for the language.

In fact, Go likes Code Clarity so much that it won't even compile if you have an unused variable declared. Or unused package imported.

I love that many of these "warnings" have become compilation errors, forcing you to do what you should already be doing: coding correctly.

Finally, `go test` is something that is more and more prevalent in different languages, and that is an ingrained testing approach.

I particularly like that go encourages you to have your test files alongside the files they're testing (so `thing.go` would be tested by `thing_test.go` in the same directory).

## What does Go suck at?

Go, like every other language, is not perfect. In fact it has some very clear flaws:

1. Development speed.
2. No real mature Game Development packages.
3. Embedded systems not really supported.
4. Error handling is weird

### Development speed

This is where Go has sacrificed everything, pretty much. By following the *less is more* principle they've created a beautiful understandable language where you have to put the more to get things done.

So pretty much everything you want to do in the language, you have to do yourself. And it will be very easy to do, yes. But it will also take time.

As an example, the language doesn't even have a `round` function in its Math library. But yeah, you can probably implement it in less than 10 lines of code, so who cares?

When you add all this, you reach a very weird conclusion: the time you save in searching documentation and stuff because the language is so easy to understand is simply traded in increased development time.

So Go is not a language for when you want to develop *fast*.

**Update!**

After some further usage and being involved with companies that are working in Go a lot, I now see I was terribly wrong in this point.

It may be that the verbosity of Go (which might be greatly reduced if generics happen) sort of offsets its simplicity and readability *when working alone*. However, when **working as a team**, these advantages are so great that the development speed is comparable to Python or Ruby, making development with this language a very fast and smooth process.

### No real GameDev

Aside from [Azul3d](https://github.com/azul3d/engine) I'm not really aware of any true 3D game engines, and it's still a very small project.

For 2D you have some other options, but nothing mature enough, really.

### Embedded Systems

Sure, you *can* use Go for Embedded Systems, just like you can use Java, but really, it's like trying to put on a very small shoe.

Just don't force it.

### Error handling is weird

This is more of a style chose, but it puts many people off. This is a typical function call with error handling in Go:

    c, err := DoSomething(foo)
    if err != nil {
        return nil, err
    }

This is much clunkier than the `try/catch` paradigm most people are used to, and for some that's enough to just scratch the language.

**Update!**

This is [being looked into](https://go.googlesource.com/proposal/+/master/design/go2draft.md)

## So... When should I use Go?

Go is, I believe, a **great team language**.

I would reccommend using it if you're beginning any project with more than 4 people and there's no language that they're "experts at" (like, everyone having 10+ years of Java experience or something).

I also think it's a **great server language**.

What I mean is that, if your software requires a lot of concurrency, web connections, and all sorts of other server shenanigans, it is a great choice.
