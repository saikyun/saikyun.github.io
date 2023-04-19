# Coding with ChatGPT

After I played around with wasm yesterday, I talked to a friend. He got me inspired to try some [ChatGPT](https://openai.com/blog/chatgpt) coding. I started out making a lisp parser in rust. It turned out pretty well, after some massage and asking it to change things. For example, it used `&str` without explicit lifetimes, which Rust didn't like. I could tell it to add the explicit lifetimes though, but now the code looked disgusting.

I bought the premium version and tried gpt4, and it instead used `String` (which seems sensible, and looks a lot nicer), but now it did tokenizing and parsing at the same time, which makes the code raise my upper lip in disgust.

It's a very different feeling from hand coding things. Like pushing a river. You can affect it, but it's hard to control, and sometimes you get chaotic whirls that the compiler and I don't like.

After the lisp parser, "we" made the evaluator. At first it had a big `match` where it would put functions like `+` as a case. But I wanted it instead to look up symbols in an environment, and have certain symbols be added to the environment by default. I asked it to do this, and it actually rewrote the code. That was pretty cool! Still some manual labour on top, but it's the sort of change that can feel hard to switch to, when you've already coded in a different style.

I should mention that from nothing to evaluator took about an hour. I think that's faster than I could have written it by hand, and it's definitely faster than it would have taken me to write it in Rust, since I'm a bit rusty.

```
cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.01s
     Running `target/debug/lisp`
List([Symbol("+"), Number(1.0), List([Symbol("*"), Number(2.0), Number(3.0)])])
Result: 7
```

I tried some other stuff, like generating example Clojure code to use as a test, something to implement in my own lisp. It was kind of hilarious, because it missed a closing parens. Even AI can't write lisp. :') [Paredit](http://danmidwood.com/content/2014/11/21/animated-paredit.html) ftw. If you haven't checked out structural programming at all, I recommend just looking at those beautiful gifs.

One thing ChatGPT has over me is how quickly it can switch between different tasks. Despite me feeling tired, I felt that I could get a momentum boost by seeing it's code, wether it was correct or not. It's like giving me a space where it already has filled out the little calls that I might have forgotten (how did I split a string with a regex in Clojure again?). It was also nice to get some Rust examples, since I haven't used it in 6 years.

After that, I tried making a card game using TypeScript. I started out having it give me examples using canvas (e.g. a function that renders playing cards), but I quickly felt that I wanted some abstractions over loading sprites and handling user input. Maybe that was wrong, but that was how I felt.

This is where I felt chatgpt became very annoying to use. I tried to have it give me examples for using PixiJS, then Phaser, then P5. And over and over again it resulted in strange typescript errors. I'm sure there might have been configuration somewhere that's strange, or I was using old examples or something. But overall it felt really unpleasant, and took way too much time. It might have more to do with the TypeScript + npm + webpack/parceljl/??? combination that easily leads to a silly amount of things that can go wrong.

After getting over the hurdle of getting something to draw a rectangle on the screen (which ended up being easiest with p5), "we" started adding things like a deck, hands of cards, a play zone etc. It felt all right, but I felt a lot less helped than when it wrote the parser. My guess is that the parser is more well defined, and it's the sort of thing that's easy to get wrong as a human, while coding game mechanics has more to do with positioning things on the screen and moving things between different collections.

Another point for ChatGPT was asking for math with natural language:

```
Can you give me an easing function in javascript, that starts out slow, then fast, then slow in the middle, then fast again?
```

```
Yes, you can use the "easeInOutQuad" easing function in JavaScript to achieve the desired effect. Here is the code for the function:

function easeInOutQuad(t, b, c, d) {
  t /= d/2;
  if (t < 1) return c/2*t*t + b;
  t--;
  return -c/2 * (t*(t-2) - 1) + b;
}
```

This is the sort of code I could figure out, but it takes me a long time and I don't enjoy it. I believe asking it for help with vector math can come in handy as well.

The most important thing I learned, is that I enjoy coding a lot more than doing code reviews. So I'll probably keep hand coding for as long as I can. :)

#100DaysToOffload