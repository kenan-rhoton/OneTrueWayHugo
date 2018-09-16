+++
date = "2017-05-20T10:18:05+02:00"
draft = false
title = "When Should I Use Rust?"
tags = ["When Should I Use","Rust"]

+++

**DISCLAIMER**: *I don't claim to be an expert on this language, so I may have made mistakes. If there is anything you would say differently or anything that is just plain wrong, please open an issue on [Github](https://github.com/kenan-rhoton/kenan-rhoton.github.io)*

[Rust](https://github.com/rust-lang/rust) is an amazing language.

True, I say every language is amazing (although begrudgingly with JavaScript), so that may not mean much, but Rust is something special.

It's a language I could imagine replacing C.

And I don't say that lightly, I'm Mr. CFanBoy. C has been in my **Top 5 Languages a Developer Needs to Know** list longer than any other, and the unofficial number 1 in my heart.

But Rust just does everything that C does, except *safer*. It helps so much to finally have a good low level programming language without worrying every single moment of my life about the dreaded `Segmentation Fault`.

But enough of that, let's get into it...

## What is Rust?

Rust is a language that will confuse you if you've never touched ML-based languages, because it seems so similar to C but things tend to not compile if you do them 100% "the C way".

This is because Rust has taken influence from a weird set of languages, such as C, Haskell and OCaml.

But aside from semantics and syntax, Rust focuses on a *safe, concurrent, practical* language.

Once again, just like in [Go](https://github.com/golang/go), Rust prevents us from really screwing up memory unless we really want to. But then we have to mark the code as `unsafe`.

Since Rust is kind enough to write down their greatest features in their website, we will talk about them one by one:

1. zero-cost abstractions
2. move semantics
3. guaranteed memory safety
4. threads without data races
5. trait-based generics
6. pattern matching
7. type inference
8. minimal runtime
9. efficient C bindings

### Zero-Cost Abstractions

Rust attempts to obey the C++ mantra:

> C++ implementations obey the zero-overhead principle: What you don’t use, you don’t pay for [Stroustrup, 1994]. And further: What you do use, you couldn’t hand code any better.
> 
> – Stroustrup

And it succeeds beautifully thanks to **Traits**.

Traits are essentially Interfaces, ways to define a certain number of expected behaviours that a Type complies with. And since they are compiled away, this means that, very much like C++, any calls to a Trait method are zero-cost.

However they are also types and can be used as an element in a struct through indirection if you need to dynamically call a method for an type unknown at compile time.

So somehow, Rust has managed to actually get the best of both worlds here...

### Move Semantics

This is a weird one for people not used to the idea: in Rust you usually move rather than copy values.

This means that this would result in a compiler error:

    let v = Box::new(5);
    println!("{}", v);
    let v2 = v;
    println!("{}", v);

Why? Because v has been moved to v2 and you can no longer use v.

Now that seems annoying, right? But don't worry! If you need to just lend a value instead of move it completely, you can just do a "borrow" by instead using `&v`.
And if you need to be able to modify the value, use `&mut v`.

What this entails is that we can always know where we can access a variable from, which is the key that brings us to our next section:

### Guaranteed Memory Safety

Read that again. Guaranteed. Memory. Safety. It's ok if you cry a little.

If that didn't blow your mind, this will: Rust uses no Garbage Collection.
And this, like many of the beautiful things of rust, is due to the move semantics.

It's simple, values can be moved or borrowed, but once they live out their scope, they are destroyed. Period.

At first it can sound scary, but really, it just means that whenever you want a value to be in a certain scope, you just move it there.

It also means that for 99% of things you won't need to ever create a Close or Destroy function :)

### Threads Without Data Races

Again Move Semantics to the rescue! Since a value can only be owned by a single scope (and thus a single thread), there are no ownership problems, but that's not all!

Remember `&v` and `&mut v`? Well, at compile time Rust makes sure that there can never exist a `&mut v` (read/write) reference when there is ANY other kind of reference to the object. However, any number of `&v` (read) references can coexist.

This mean no race conditions. Whoa.

### Trait-based generics

We already touched on this, but the key here is very simple: you can use Traits as Types that satisfy an Interface. Which means that you can declare a function for all of those Types at once.

For example:

    fn print_hash<T: Hash>(t: &T) {
        println!("The hash is {}", t.hash())
    }

`t` can be a borrow (note the `&`) of any Type which implements the Hash Trait.

### Pattern matching

Everything is an expression in Rust. This mean this is valid code:

    let (x, y, z) = (5, "Potatoes", false);

And that you can declare functions such as:

    fn compare_hash<T: Hash>(t: &T, t2: &T) -> bool

Where, you guessed right, not only do both t and t2 need to implement Hash, but they must be the same Type.

### Minimal runtime


Rust is built on LLVM and it's optimized like crazy. All those weird rules about moving and borrowing, and the way Traits work allow the runtime to be a very efficient thing that pretty much needs to do nothing but some initialization setting up a heap, some guards and backtraces.

This means Rust is stupidly fast. C-levels of fast. Like whoa.

### Efficient C bindings

Rust is not here to displace C, although it very well might.

The truth is that, especially at low level, most things are C. So interfacing correctly with C is a must, really, if you want to be compatible with the existent way of doing things.

This also means that it's simple to make a Rust extension to a C application, and so I feel like transitioning things from C to Rust is quite a nice process. [Tor](https://lists.torproject.org/pipermail/tor-dev/2017-March/012088.html) is doing it :)

## What does Rust suck at?

All languages are amazing, but I've yet to find one that is perfect, and Rust is no exception.

Although its problem are not as glaring as other programming languages which may or may not be called JavaScript, they still exist and must be considered:

1. Rust is hard to learn and master
2. Rust is young and doesn't have as many libraries as you'd want
3. Not really for the web

### Hard to Learn and Master

Unless you're lucky (or crazy) enough to already be profficient in an ML language, a C language and a functional language, chances are Rust is gonna look downright weird to you.

You will probably take a couple of months until you finally stop being surprised at random compiler errors for things that you're *sure* should be working.

This also means you have to be reasonably sure you actually want to use Rust for something before getting on to learn it...

However, you really should learn Rust anyway, so get on it!

### Not enought Libraries!

The language is young, still, so this will probably be a nonissue in a few years, and a large number of libraries are appearing every day (in part thanks to [Redox](https://github.com/redox/redox), a complete functional OS written in Rust. Yes, I said an OS).

The fact remains that Rust is still in its infancy, and some things just aren't available. You probably can't reasonably create a TripleA game in Rust (yet).

So if you're building something complex, that might turn you away, although you should consider contributing libraries yourself! :)

### Not for the web

Yes, [Iron](https://github.com/iron/iron/) exists. You technically CAN develop a Web App in Rust. But really, should you? It's not designed for it. At all.

And this is probably its greatest problem nowadays, since 90% of everything being done is in the Web...

## So... When should I use Rust?

If you need to create a fast, robust, complex app, Rust has your back.

Need a new accounting program? Rust.
Something to coordinate signals between different programs? Rust.
A driver for that new piece of hardware your company has been building? Rust, please, the world will thank you for it.

Rust: the safe, fast, concurrent language.
