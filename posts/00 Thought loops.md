# Hello

Inspired by [Fredrik Björeman](https://bjoreman.com) I decided to create my own blog. In his podcast [Kodsnack](https://kodsnack.se/508/) he and [Kristoffer](https://6510.nu/@krig) talks about getting stuff out without thinking too much.

I felt this very hard, as I've been stuck in some thought loops lately. If I were to describe it as shortly as I could, this would be my attempt:

1. I want to be able to create graphical applications and games, that can run on as many platforms as possible, with live coding capabilities

2. To fulfill this, I created [Freja](http://github.com/saikyun/freja), a code editor that can be modified withing itself, and therefore create GUIs and games without ever closing the applications

    2.1. Well, that was the idea anyway, but I still have problems like ending up in an infinite loop and needing to restart

    2.2. The bigger issue however, is that the GUI lib I wrote doesn't work well enough. Tons of tiny bugs that pop up whenever I try to create new GUI

    2.3. I also don't quite agree with the language I use, [Janet](https://janet-lang.org), which is a super cozy lisp, but has some other ideas about live coding / redefining functions during runtime, which are not hopeless to overcome, but often a bit in the way. This is in no way the fault of the language, it just has slightly different goals than I have.

3. Despair

4. I've tried Unity and Godot, and while I dislike the former (extremely sluggish, and the minor point that C# feels like a nice, safe car but sooo boring -- where is my meta programming!?), I can withstand the latter. It's snappy and nice, has basic hot reload, but I personally feel the OOPiness (specifically no interfaces and tons of inheritance) makes for a less cozy environment for me.

5. Now I'm standing here, wondering what to do with my situation. I feel like I don't have a cozy place to code, but I'm not sure I'm ready to rewrite the GUI library. I'm also thinking about writing it in C, a language which I've gotten a lot more love for, since learning that hot reloading DLLs is surprisingly viable. But C lacks some things I want (multiple dispatch, dynamic arrays). I've tried to remedy this with macros, but it still feels a bit icky. Like I'm trying to make the language be something it's not.

So here I am. I've experimented a lot, e.g. making C more dynamic (changing structs during runtime), compiling lisp to C, playing around with type unification. But I have no clue where to go.

#100DaysToOffload