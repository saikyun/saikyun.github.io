# [Coding](#coding)

I like to have a feeling of flow when I code. The best I've felt generally is using Clojure. Here are the main things I think helps feeling flow with Clojure:

- unrestricted live coding with a repl
    - I could rewrite clojure.core (the standard library) while my application was running. that power is very useful when experimenting and modifying functions and trying them again. you can set up your state in a perfect way for your experiment, then modify the function until it outputs what you expect.
        - this is possible with TDD as well, but sometimes it can be hard/take a long time to set up the state necessary for TDD (maybe the state is hard to serialize), making it more practical to just run your application, make it go into the state you want (e.g. in a game, run to the place where you want to try something), then run/modify/run the function until it does the right thing
            - an alternative solution to repl'ing here is just having all state be serializeable and have a super fast compiler. I believe that setup would be hard to discern from repl'ing. this is probably how I'd do it with a compiled language :)
    - if you don't understand what the above means, it just means that you can modify your program while it is running. say you have an animation that you want to tweak, let's say the bounce of a button. let's also say that the button is only visible after you have filled in some state (e.g. a submit button that won't bounce until you have filled out a form). with live coding, you can modify the code, and instantly see how the animation changes, while the form is still filled in. you can also "ask questions", i.e. write code to query the state ("what name is currently inputted?" or "does the email fulfil `correct-email?`?"). I still haven't figured out a nice way to express this succintly. it might be something that cannot be told, only shown. if that is the case, [here's one place where I try to show it](https://www.youtube.com/watch?v=k1FMk7Js2Rw)
- immutable data
    - it just turns code cleaner, in general. in my current C project I modify pointers which in hindsight has turned a lot of my project to mush
- [paredit](http://danmidwood.com/content/2014/11/21/animated-paredit.html)
    - the elegance of paredit is being able to think about code in a more abstract way. being able to flip two branches of an `if`, or changing the order of two elements in a vector, and having those commands use the same hotkey is just so nice when you get into it (`transpose-sexps` (this is emacs, not paredit, but paredit adds a bunch more -- from vscode's perspective it's all paredit))
- libraries that seldom move
    - clojure has a culture of adding onto rather than modifying. Rich Hickey has a [good talk](https://www.youtube.com/watch?v=oyLBGkS5ICk) on why modifying your functions often means breaking them.
    - this leads to more calm when updating libraries

