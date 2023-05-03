# [Compiling Lisp to C](#compiling-lisp-to-c)

Today I got some time to work a bit more on the compiler. It's been a two week break, mostly because of focusing on GTD stuff, having meetings with work people last week, my wife going to Stockholm for a couple of days, my wife being sick, me trying to actually do the stuff I wrote in my Orthodox GTD Journal.

I'm pretty happy though, because my home is surprisingly clean, and I finally ordered a portable laptop stand that I've been wanting for years. I've also bought a Planck EZ from a nice guy / super star (perhaps most famous for his [shorts video](https://www.youtube.com/watch?v=Fy0aCDmgnxg)). When it has arrived I'll proudly take a photo of my glorious set up. Did I mention I bought wooden wrist support as well?

So, with all that sort of figured out, I finally felt the peace of mind to sit down with my lisp again.

When I last left of, I had almost fulfilled the goal of compiling

```
(defn fac [n]
  (if (<= n 1)
  1
  (* n (fac (- n 1)))))
```

to

```
int fac(n) {
  int res;
  if (n <= 1) {
      res = 1;
  } else {
      res = (n * fac(n - 1));
  }
  return res;
}
```

The stuff that was missing was:
1. Figuring out what should get a `;` at the end (e.g. not `if`)
2. Calling user defined functions

I fixed 1. pretty easily, thanks to having both thought and talked about the problem with my friend. 2. was pretty easy to, for now I just assume people fill in the right names for everything and try to call it.

After that, I got it to compile it to C and run the resulting source in the same process using libttc. Very cool! :D

I did know there were some problems though. So after the initial success, I wrote some down:
* Types (right now only `int` is supported)
* While-loops
* Structs

I decided to tackle types first, and thanks to the great resource in janet's [cgen](https://github.com/janet-lang/jpm/blob/476cbebbb08e92032ca6ae0bb842c199fe8edd3f//jpm/cgen.janet), I figured I could just use explicit types for now, in the ast having the form of `(int num)`, so a defn would look like: `(defn add [(int x) (int y)] int)`. I thought I could make it look a bit nicer in my source, so I decided on this syntax for now:

```
(defn strlen-plus-n
  [str :string num :int] :int
  (+ num (strlen str)))
```

Of course, the goal is to add type inference later, but since the C ast will need the types explicitly, to make sure that worked first, it felt easiest to start with explicit types.

Anyway, after hacking just a bit, mainly changing how `defn` ast nodes are transformed (specifically the arguments), I managed to compile the above to:

```c
int strlen_plus_n(char* str, int num) {
  return num + strlen(str);
}
```

Yay! :D

Soon I might actually be able to compile enough C to write a little program. :)

_#100DaysToOffload - Please say hi on [mastodon.social/@saikyun](https://mastodon.social/@saikyun). :)_