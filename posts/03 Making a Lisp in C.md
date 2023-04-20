# Making a Lisp in C

Today I started working on a lisp in c. I want the lisp to compile to C. I've tried it before, but the first time I got stuck on figuring out what types things should be (assuming I don't want to fill out all the types all the time in lisp). Since then I've done some basic work on [unification](https://github.com/saikyun/unification/tree/10b19ae798b508127fb54fa68ed218c99bdd23f4) / type inference. When I tried my first lisp in c, I only found research papers about unification, which I had trouble understanding. I wasn't sure how to learn how to read them either, and ended up listening to [Tractatus Logico-Philosophicus](https://en.wikipedia.org/wiki/Tractatus_Logico-Philosophicus). It didn't work very well in audiobook form, and it definitely did not help me understand how to read science papers with strange symbols.

Since then, a friend showed me https://eli.thegreenplace.net/2018/unification/ which talked my language a lot better. So I was able to do the basic stuff, finally.

I did start on [another lisp in c](https://github.com/saikyun/lisp-to-c) after writing that unification stuff. While I did manage to compile some C from lisp, I got a bit stuck trying to figure out how enable macros (i.e. running lisp while still being in the compilation phase). At least I think that's what happened. I started some work on doing both `eval` and `compile`, i.e. an interpreter _and_ a compiler. But it seemed like I would have to write a lot of the same code over and over again.

What I've figured out now is that I somehow want to be able to:

1. Compile lisp code to C
2. Evaluate lisp code while in the compilation phase, using the same code as step 1. does

This seemed tricky, since I didn't know of a way to get `eval` for C. Then I remembered that my friend told me about [tcc](https://bellard.org/tcc/). tcc is a tiny c compiler, that is easy to build and bundle with your project. Even in the 2nd iteration, I figured I'd use tcc to generate dlls to facilitate live coding. What I didn't realize back then, but figured out now when reading the docs, is that you can _use tcc as a library_, and _compile functions to memory_.

[I tried that.](https://github.com/saikyun/libtcc-example) It's very awesome. Suddenly you have eval in C.

This means that if I encounter a macro during compilation, I can call some libtcc functions, and get some results, and then use those results when continuing compilation. Pretty cool!

I'm also guessing it'll make live coding ever so slightly faster, since I won't have to start a separate process, compile a dll/so to disk, `dlload` that dll, e.t.c.

## Third time's the charm

So now I'm starting again, this time using only C, and trying to make sure everything works with tcc. Sadly I had some [problems building binaries](https://lists.nongnu.org/archive/html/tinycc-devel/2023-04/msg00029.html) on my macbook air m2, but `tcc -run` does work. So hopefully it can be sorted out.

Ofc what I probably "should" do is either use llvm, or go all the way and just interact with assembly directly, but both those have their problems.

First off, llvm just seems to have slower compile times overall than tcc. Of course it then wins hugely during runtime, but that's not important for `eval`. My language should be able to AOT compile as well, and then I'd use clang / gcc / cl. But when coding, I figure tcc will speed up development a lot.

Doing something with assembly, instead of having the middle step of C, appeals to me a lot, but I know next to nothing about assembly, while I can do basic stuff in C. And even if I were to learn some sort of assembly, I would be tied hard to whatever platform I decided to learn. With tcc it seems feasibly to build/eval on all desktop platforms, and maybe the browser and phones.

And since my language will build to C in the end, I figure that when you're done coding and want to build binaries, it should be possible to build them for all manners of platforms, including consoles. You lose `eval`, but while it's a bit boring to lose it, it's not as crucial as it is while developing.

So far I've built the [tokenizer](https://app.slack.com/client/T024SRSB2/C011CD5P1S6). Not much to look at yet. But hopefully it won't be too long until I can call some C functions using my lisp. :)

#100DaysToOffload