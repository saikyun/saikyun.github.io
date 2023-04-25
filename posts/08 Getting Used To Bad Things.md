# [Getting used to bad things](#getting-used-to-bad-things)

I think there are more people than me who are good at getting used to bad things.

I used to code lisp in emacs, and what's amazing about it, is that you can use [Paredit](http://danmidwood.com/content/2014/11/21/animated-paredit.html) (and other structural editing tools, like those built into emacs) which let's you treat the code like a branching road where you can move towns and lakes around, rather than erase individual characters. The most obvious example in my mind are languages where `,` separates "things", e.g.:

```
int sum(int curr, int acc)
```

In this situation, if you want to switch the place of `int curr` and `int acc`, you have to do this awkward dance of selecting `acc`, cutting it, moving the cursor to `curr`, paste it, select `curr`, cut it, move the cursor back to where `acc` used to be, paste. If there were no `,`, at least you could just select and cut the whole `int acc`, move the cursor to right after `(`, and paste, hit space, and remove the trailing space at the end. There are many variants on this, and if you're anything like me, you notice when these awkward things happen. And there's not really a clean solution.

[That's not true in lisp.](https://calva.io/images/paredit/transpose.gif)

You just do a single command, `transpose-sexp` (preferably bound to a hotkey). And when you want to move multiple expressions that are in the same block, let's say you have code like this: `(curr :int acc :int)`, then at least you can stand in the middle, hit `Ctrl+K` which cuts until right before the closing `)`, then move to the beginning of the expression, then paste. At least you don't have to fiddle with selecting single characters.

But I've gotten used to not having it, after sitting in C-based languages for more than a year. And it's very sad.

Of course there are a lot worse things to get used to, like depression, abuse and plastic accumulating in our nature.

Still though, I wonder if there's a connection. If you allow yourself to get used to one thing that you can affect, but don't. Do you get better at getting used to bad things?

_#100DaysToOffload - Please say hi on [mastodon.social/@saikyun](https://mastodon.social/@saikyun). :)_