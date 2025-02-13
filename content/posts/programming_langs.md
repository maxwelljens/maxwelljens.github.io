+++
title = "Thoughts on Programming Languages"
date = 2022-12-12
type = "post"
tags = ["programming"]
image = "/thoughts_on_programming_languages/media_card.webp"
+++

There are a lot of programming languages, but often they are talked of in terms of what realistic applications they
have in the job market. Seldom is there prose about their quality as such; independent of their popularity and
application. Here's some of my thoughts.

## Quality versus utility

As most software engineers know, there is not really any correlation between the quality of a language and its
popularity. There is however a correlation between popularity and utility. Python might not be the best language ever
made, but any design flaws it has are offset, in the eyes of most, by the fact that it has libraries for everything.
Why? Because it is in top three most popular languages, somewhere around C and Java. Therefore any issue one might
encounter probably already has a complete solution in the form of a third-party library. This means that Python has
extremely high utility, even if there are design issues with the language that can get in the way of common usage;
while writing code.

Java is an even better example of this, as it is
[demonstrably](https://www.theregister.com/2013/01/31/java_security_update/) one of the most incompetently designed
languages in common use. Some people would probably argue it is the worst, although I do not have personal experience
with it to make that much of a bold statement. From my research, however, I can tell Java is terrible and should be
avoided if possible. Not the least because the company behind it, Oracle, is possibly [one of the most predatory
companies](https://www.realclearpolicy.com/articles/2021/12/21/washington_antitrust_efforts_ignore_predatory_practices_of_big_software_vendors_808739.html)
on the planet, and will siphon astronomical amounts of funds from any company that uses any of their Java
virtualisation technologies in any capacity.

Still, quality of Java and even its big vendor are entirely irrelevant, and Java continues to be one of the most widely
used programming languages. Why is that? Well, the answer is rather simple and is applicable to many other widely
used programming languages: *clout of the past*. To turn a rather long story short: Java (not under Oracle at the time)
was taking the software engineering world by storm, as a platform-independent alternative to C and C++. Most notable
marketing gimmick was the audacious claim *"write once, run anywhere"*. It was also riding a then-trendy fad of
object-oriented programming as being the king solution to every programming problem. Of course, as we found out quite a
while ago, object-oriented programming is not a be-all and end-all solution, and Java was not even that great at
[implementing it](https://www.geeksforgeeks.org/java-not-purely-object-oriented-language/) to begin with, especially
when compared to Python, that does everything Java ostensibly does. Regardless, the driving force was not quality of
the language. It was the extensive marketing behind it, and it was sold to managers, not software engineers. Whether
software engineers liked it or not, managers said Java was the new company tool of choice, and they had to put up with
it. The language remains popular, because, even if aforementiomed managers became disillusioned, which they most likely
did, as they saw that company bottom line remained largely unaffected, **they were now stuck with Java
infrastructure**. As with almost anything else, it is easier to build something than to replace existing systems. This
is where Oracle gets you with astronomical bills that nearly bankrupt any company, but that is veering off topic.

Similar story applies to programming languages like C# or Swift, except instead of a marketing force driving its
popularity, it is the fact that C# is the premier solution for programming software for Windows. Same with Swift, but
for macOS. Since nearly everyone uses Windows and macOS, C# and Swift are widely used as well, and Swift is not even
that difficult to [use outside of the macOS ecosystem](https://linuxconfig.org/how-to-install-swift-on-ubuntu-20-04).
Surprising, considering it's an Apple product.

In short, most programming languages are popular not because of their design merits, but because they had some success
in the past that *forces* their use today. Even better examples than Java of this are Ada, COBOL, and especially
[JavaScript](https://www.youtube.com/watch?v=2pL28CcEijU). Although JavaScript is not old like Ada or COBOL, it is
exclusively an artifact of the early Internet, and it shows that it was [made in two weeks by an overworked engineer at
Mozilla](https://github.com/denysdovhan/wtfjs). Alternatively, programming languages are popular by mandate of
companies that run the most popular operating systems, such as Microsoft with C# or Apple with Swift.

Logically, the converse is true: there are many great programming languages with outstanding design characteristics,
but "nobody" uses them, rendering them useless. **It's a chicken and egg problem**: nobody uses them because nobody
uses them, and because they don't have abundant libraries for solving common problems, because nobody uses them. You
get the idea. Most languages do not ever get past the hobby stage for this reason. One of the languages I will give my
thoughts on sort of fits into this category. Whenever there is a major problem in the IT industry, the first available
solution is what becomes the irreplacable solution. Those solutions become irreplacable, because, as alluded to
earlier, systems are much more easily built than replaced outright. Python was not particularly popular until it was
found to be the "killer app" for prototyping in STEM fields.

Either way, no matter how you frame the situation, quality of a language itself and its utility do not go hand in hand.
In my eyes, this is a big reason why there is a larger entry barrier than necessary to software engineering. Nobody
new to software engineering needs to learn Java or JavaScript, but because these languages are disproportionately
popular, newcomers might be under the very mistaken impression that somehow they are representative of quality. They
are not. The languages I will talk about will be described in terms of quality, and which ones are good for newcomers.

## Good programming languages

To begin with, I will look at some programming languages that I consider to be good. They appear in no particular
order, but any languages I will mention I had personal extensive experience with, and do not base it off hearsay from
other sources of information.

### Rust

Rust appears kind of scary, and it somewhat is. Linus Torvalds said that Rust was really complex, arguing that C is a
lot simpler. The Rust compiler is certainly a beast, throwing errors at you at seemingly every new line you write. To
begin with, yes, it is absolutely unforgiving and gruellingly difficult for a beginner. The learning curve is
infamously steep, but, once you become acquainted with the compiler, you start to realise that it is basically guiding
you how to write properly imperative software.

Rust is intended for systems programming, and it is indeed fast. [In some cases faster than C and
C++](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/rust.html). What might be surprising is that
it is easy enough to use for even the simplest scripts, once you get past the initial learning barrier. Other than
hardcore programmers like Terry A. Davis or Chris Sawyer, nobody would really want to use C or even C++ to program
everything. If system administrators need a script, they will naturally resort to either Bash or Python, since the
machine-level mechanisms are much more abstracted away, reducing the cognitive workload. Rust, however, is sufficiently
high-level that it might be not much of a migraine to get something simple in it going. This would depend largely on
the person, of course, but Rust is unmistakably better than C and C++ in several domains, with no sacrifice of raw
efficiency.

While in C and C++ memory management is manual, Rust utilises a unique mechanism known as the "[borrow
checker](https://doc.rust-lang.org/1.8.0/book/references-and-borrowing.html)". Although it is the main source of
compiler throwing errors at you at every line, it means that the compiler is able to reason about the safety of your
program at compile time. C and C++ compilers make exactly *zero guarantees* about the safety of your code at compile
time, and you have to write systems checking the correctness of your program yourself. Rust, on the contrary,
eliminates [entire categories of security vulnerabilities and memory errors at compile
time](https://stackoverflow.com/questions/36136201/how-does-rust-guarantee-memory-safety-and-prevent-segfaults/36137381#36137381).
With the exception of writing code in an `unsafe { ... }` block, you simply cannot compile a program that would produce
memory insecurities: buffer overflows, buffer over-reads, null pointer dereferences, double frees, invalid frees, and
so on. It will all be a compiler error if your code contains behaviour that would lead to that.

A question you might be asking yourself: why bother learning Rust if it's so hard and low-level? The answer is really
rather simple: **you learn how computers work at (almost) the most foundational level**. Although Python is markedly
easier to start off with, it doesn't teach you how computers work. Because it doesn't teach you how computers work, it
also doesn't give you a reference point for why certain programming practices exist. Not always, but most programming
practices exist for efficiency and clarity. Sometimes efficient code is also clear code. Using
"[varargs](https://stackabuse.com/variable-length-arguments-in-python-with-args-and-kwargs/)" works well in Python
because of [duck typing](https://wikiless.tiekoetter.com/wiki/Duck_typing?lang=en), but in many other programming
languages, particularly [strictly typed](https://wikiless.tiekoetter.com/wiki/Strong_and_weak_typing?lang=en) ones, it
is a bad idea or sometimes even impossible due to compiler restrictions. Using lists is almost always the better
alternative, but because Python strongly depends on and encourages duck typing, these ideas will escape all newcomers
to software engineering that choose Python as their first language.

Additionally, the Rust compiler is so sophisticated that it gives you specific errors about issues in your code, like
so:

```
5 |     let scores = inputs().iter().map(|(a, b)| {
  |                  ^^^^^^^^ creates a temporary which is freed while still in use
6 |         a + b
7 |     });
  |       - temporary value is freed at the end of this statement
8 |     println!("{}", scores.sum::<i32>());
  |                    ------ borrow later used here
  help: consider using a `let` binding to create a longer lived value
  |
5 ~     let binding = inputs();
6 ~     let scores = binding.iter().map(|(a, b)| {
  |

For more information about this error, try `rustc --explain E0716`.
```

Sometimes, as in the error message above, the compiler even gives you a potential solution to the problem. The Rust
compiler is very smart, and in a lot of ways can act as a guide for you in learning how low-level imperative
programming works. The Python environment is nowhere near as smart and, for a language priding itself on being beginner
friendly, it oftentimes outputs obtuse error messages that are not at all obvious without looking them up on the
Internet.

It is worth learning Rust, even if you figure out the compiler and still think the cognitive load is too big. You would
get a lot out of the experience. You would get a far greater appreciation of what goes on "beneath the hood" of a
computer program, an experience which is severely lacking in today's IT world. It's one of the big reasons behind why
[Electron](https://archive.ph/1UuE9) is deemed an acceptable solution in any domain of general computing whatsoever,
even though it is demonstrably one of the worst software frameworks to ever exist. No, 275 MB for an [executable that
prints "Hello,
world!"](https://stackoverflow.com/questions/59731319/how-can-i-reduce-my-275mb-hello-world-electron-package-size) is
not acceptable software design. It's [software equivalent of
cancer](https://wikiless.tiekoetter.com/wiki/Wirth%27s_law?lang=en), so why would you want that on your computer? This
is why I think Rust is important: it takes C++ into the 21st century, but without sacrificing performance, and
therefore is a viable tool for teaching people how computers work. Tech illiteracy in software engineering is actually
staggering, and more people need to see Rust, so that they can see the error of their ways.

### Go

Although often people compare Rust to Go, Go is not a systems programming language. Rather, it is Google's in-house
solution for Google problems, but has been open-source for a while now, with explosive popularity, due to its big
backer.

What are Google problems, then? That would be cloud and other networking solutions. Go is geared towards that in its
principal design. Easy multi-threading, easy concurrency, garbage collection for development brevity, very simple
ruleset, and designed by one of the main inspirations of C, Ken Thompson. The language is explicitly designed to be as
close as possible to C, but garbage collected; cognitive load significantly lessened during development. It even
supports generics, unlike C. Despite being garbage collected, it is not that much slower than [the other top
languages](https://benchmarksgame-team.pages.debian.net/benchmarksgame/box-plot-summary-charts.html). Given that it
compiles dependency-free binaries, like Rust, Go is excellent not just in the domain of networking, but as a general
computing solution. Where performance is not of paramount importance, Go shines, and many programs that I use on a
daily basis have been developed with it:

* [fzf](https://github.com/junegunn/fzf) - fuzzy search finder, which I use in my Neovim config for any file indexing.
* [gitea](https://github.com/go-gitea/gitea) - how I used to host a web-facing git instance.
* [lazygit](https://github.com/jesseduffield/lazygit) - more sane git management.
* [croc](https://github.com/schollz/croc) - trivial transfer between machines on the same LAN.

For a programming language primarily designed to solve Google cloud problems, it does a good job at most of everything
else. Here's an example of a program that sorts strings and integers:

```go
package main

import (
  "fmt"
  "sort"
)

func main() {
  strs := []string{"c", "a", "b"}
  sort.Strings(strs)
  fmt.Println("Strings:", strs)

  ints := []int{7, 2, 4}
  sort.Ints(ints)
  fmt.Println("Ints:   ", ints)

  s := sort.IntsAreSorted(ints)
  fmt.Println("Sorted: ", s)
}
```

With garbage collection, type inference, built-in error interface, generics, closures, less verbose for-loops, and many
other small features add up to a significantly more concise imperative language, without complete sacrifice of
performance and ability to make dependency-free binaries. That is why the above code is quite concise, compared to C
and similar languages.

### Nim

Nim is a powerful beast. It is more than likely the most feature-rich programming language I am aware of.

* Compiles dependency-free binaries.
* Cross-compiles to most major platforms, [even Nintendo
  Switch](https://nim-lang.org/docs/nimc.html#crossminuscompilation-for-nintendo-switch).
* Is garbage-collected, [but has performance very near C and C++](https://github.com/kostya/benchmarks), **without
  resorting to manual memory management**!
* Easy, built-in multi-threading and concurrency tools.
* Strictly typed with compile-time type checks.
* Compile-time function evaluation.
* Object-oriented faculties, including inheritance and mutually recursive types.
* Transpiles to C, C++, and JavaScript if needed.
* Is compiled in itself, and can be
  [metaprogrammed](https://stackoverflow.com/questions/2565572/metaprogramming-self-explanatory-code-tutorials-articles-books/2566561#2566561)
  without restriction.
* Syntax strongly inspired by Python; no curly brackets needed.
* Syntax is extremely concise thanks to solid type inference and extensive syntactic sugar.
* ... a lot more.

Here's an example taken from Nim's official website:

```nim
import std/strformat

type
  Person = object
    name: string
    age: Natural # Ensures the age is positive

let people = [
  Person(name: "John", age: 45),
  Person(name: "Kate", age: 30)
]

for person in people:
  # Type-safe string interpolation,
  # evaluated at compile time.
  echo(fmt"{person.name} is {person.age} years old")

# Thanks to Nim's 'iterator' and 'yield' constructs,
# iterators are as easy to write as ordinary
# functions. They are compiled to inline loops.
iterator oddNumbers[Idx, T](a: array[Idx, T]): T =
  for x in a:
    if x mod 2 == 1:
      yield x

for odd in oddNumbers([3, 6, 9, 12, 15, 18]):
  echo odd

# Use Nim's macro system to transform a dense
# data-centric description of x86 instructions
# into lookup tables that are used by
# assemblers and JITs.
import macros, strutils

macro toLookupTable(data: static[string]): untyped =
  result = newTree(nnkBracket)
  for w in data.split(';'):
    result.add newLit(w)

const
  data = "mov;btc;cli;xor"
  opcodes = toLookupTable(data)

for o in opcodes:
  echo o
```

How all of these features are implemented without markedly impacting performance is unknown to me. In all technical
aspects it is an impressive language. As far as imperative languages go, I consider it to be the most sophisticated,
advanced, yet pleasant language to program in. Many languages implement several of the aforementioned features: Python,
C#, Swift, Go, and many others. None of them have *all* of these features, however, which is what distinguishes Nim
from any other that I have seen.

I had so much joy programming in Nim that they led me to my first ever minimally viable projects:
[nimjack](https://maxwelljensen.no/git/maxwelljensen/nimjack) and
[nimchain](https://maxwelljensen.no/git/maxwelljensen/nimchain). Before these, I would play around with Python, but
nothing about Python would really stick with me. It had overwhelming complexity, obscure bugs that make no sense, far
too many ways to do a single common task, and more. It was an unpleasant experience for someone to just start with. Nim
has a ton of features, but I always felt like there was only one, sometimes two, logical way of solving a logical
problem. This is where I feel like Python and my other "good programming languages" list diverge significantly.

The only issue with Nim that is going to make it an unrealistic option in most environments is the fact that it is
relatively unknown; unpopular. There is progressively more awareness surrounding it, if slowly. Latest uptick was a
YouTube video released by Fireship, a substantially large channel about programming, titled [*"Nim in 100
Seconds"*](https://www.youtube.com/watch?v=WHyOHQ_GkNo). According to comments under the video, Nim has found its way
into ethical hacking, and in new startup companies. That being said, it is still vastly less popular than Rust and Go,
which are already only moderately popular when compared to Python, C, and C++. Nevertheless, the merits of Nim cannot
be overstated, and I hope it becomes a standard in the future for programming. It puts the "multi" in "multi-paradigm
programming language" like no other.

### Haskell

While the aforementioned languages are predominantly imperative, Haskell is a *purely* functional language. Put
differently, it is not a multi-paradigm programming language. Although most multi-paradigm programming languages
support functional paradigms, they are just that: support. They are not a requirement, unlike Haskell, where the only
paradigm accepted is functional programming. What does that look like in practice?

```haskell
quicksort :: (Ord a) => [a] -> [a]  
quicksort [] = []  
quicksort (x:xs) =   
  let smallerSorted = quicksort [a | a <- xs, a <= x]  
      biggerSorted = quicksort [a | a <- xs, a > x]  
  in  smallerSorted ++ [x] ++ biggerSorted  
```

Alright, that looks pretty alien. What you are looking at is a [quicksort
algorithm](https://www.geeksforgeeks.org/quick-sort/), although technically it is not real quicksort, since data is not
mutated [in-place](https://wikiless.tiekoetter.com/wiki/In-place_algorithm?lang=en). In fact, Haskell explicitly
prohibits mutation, meaning only immutable variables are allowed. The whole explanation behind above code can be found
[here](http://learnyouahaskell.com/recursion#quick-sort), but the essence of the language is that you code *what* you
want, not *how* you want something. This makes Haskell a *declarative* language, as opposed to an *imperative* one. You
declare what the output of `quicksort` is, rather than what `quicksort` does. As you can imagine, this makes Haskell a
very high-level language, but it looks nothing like Python, which is another distinctly high-level language. This is
because Python is an imperative language. Compare the same algorithm in Python:

```python
def partition(array, begin, end):
  pivot = begin
  for i in range(begin+1, end+1):
    if array[i] <= array[begin]:
      pivot += 1
      array[i], array[pivot] = array[pivot], array[i]
  array[pivot], array[begin] = array[begin], array[pivot]
  return pivot

def quicksort(array, begin=0, end=None):
  if end is None:
    end = len(array) - 1
  def _quicksort(array, begin, end):
    if begin >= end:
      return
    pivot = partition(array, begin, end)
    _quicksort(array, begin, pivot-1)
    _quicksort(array, pivot+1, end)
  return _quicksort(array, begin, end)
```

Although this one is a real quicksort algorithm, since data is mutated in-place, we can clearly see that the code is a
lot longer than in the Haskell example, since we have to define all the steps involved in the algorithm. We are
commanding the program how to act, rather than what the output is. For this reason, the Haskell example is a lot more
concise, and conciseness is where functional programming shines.

For me, concise code is the most important matter when writing code. Although one can alleviate the downsides of long
code with proper documentation, it is best to just write code so simple that ideally documentation is unneeded.
Functional programming helps with that, because then you can reason about any function only in terms of input and
output. You might be tempted to say that you should keep functions and code short anyway, regardless of language. Have
one function do one thing only, and do it well. I totally agree, but that is an integral tenet of functional
programming. Most people in some capacity or another gravitate towards functional programming without even knowing it.
Although [monads and monadic I/O](https://wikiless.tiekoetter.com/wiki/Monad_(functional_programming)?lang=en) sound
completely alien, and most software engineers never heard the word "monad" in their life before, [they know what it
is](https://wikiless.tiekoetter.com/wiki/Option_type?lang=en). They just don't know it is called a monad, as it's a
word taken from a subdomain of mathematics known as category theory. Given that Haskell was developed by committee,
explicitly for the purposes of making the all-father of functional programming, it is no surprise that Haskell
terminology is going to be strange. It also doesn't help that the committee consisted mainly of mathematicians. Even
those who were not, such as Sir Simon Peyton Jones, still insisted on using mathematical terminology rather than what
would become more standard in the programming sphere. After all, the language is named after [Haskell
Curry](https://wikiless.tiekoetter.com/wiki/Haskell_Curry?lang=en), who was a mathematician. I strongly recommend
watching [*"The Haskell journey: Watt on earth were were thinking?"*](https://www.youtube.com/watch?v=re96UgMk6GQ) by
Sir Simon Peyton Jones at Churchill College, University of Cambridge in 2017, for a rundown on a rather unusual
development of Haskell. Sir Jones is a good presenter.

#### Declarative and functional programming

As for the language itself, it is worth learning Haskell. Much like how Rust is a very good introduction into low-level
imperative programming, Haskell is, inversely, a very good introduction into what high-level declarative programming
can look like. It is also purely functional, so you are forced into thinking about logical problems exclusively in
those terms. It gives you a fresh perspective into programming. For me, learning Haskell was like learning programming
anew; all over again. One of my friends made an interesting statement about Haskell, upon learning about it: *"this is
what I thought programming was before I went into Python and C#"*, paraphrased. I agree. I think high-level programming
languages should be a lot less like Python or JavaScript and a lot more like Haskell.

A common response to Haskell is: if you are not able to mutate variables at all, how can you do anything? The answer is
that you can do everything you can in an imperative language, just without mutation. Diesel engines don't need spark
plugs to combust fuel, and in the same vein Haskell doesn't need mutation to do its work. The reason why Haskell does
away with something so taken for granted as variable mutability is simply to prevent
[side-effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science)) and keep [functions
pure](https://en.wikipedia.org/wiki/Pure_function). Why is this important? It is so that the compiler can reason about
everything a function does. It is a concept known as *referential transparency*: the idea that any function will yield
expected results every time it is run. In mathematics, that would be known as proving a statement. Therefore, a
function that writes to hard drive is impure, because it is not guaranteed that every time it is run the result will be
the same. The hard disk can jam, run out of power, or other issues. Granted, at a sufficiently granular level,
everything in a computer is a side-effect. Writing to CPU register is a side-effect. Therefore functional purity in
terms of Haskell refers to the environment of I/O versus non-I/O. Functions that depend on I/O are impure, and
therefore any number, string, float, or any other type that interacts with I/O will be given the type `IO a`, which is
a type of monad (but it is not all monads). You can never escape this monad, or any other monad, which is the whole
point of monads; monadic I/O. As far as I know, no imperative language enforces such a system in their
compiler/interpreter.

Ultimately all of this might sound familiar to someone who has worked with software engineering at a professional
level. You *do* want to keep side-effects to a minimum, because referential transparency isn't just for the benefit of
the machine, it is also a benefit to the man behind the code. You *do* want to know what the program is doing, and
referential transparency is a good start for making that happen. Well, at least if you are a good software engineer.
The only difference between your coding practices and Haskell is that Haskell enforces it with its syntax and compiler.

Lastly, you might be asking yourself: what can the compiler reason about with this referential transparency? For
instance, parallelising your Haskell code [becomes
trivial](https://book.realworldhaskell.org/read/concurrent-and-multicore-programming.html). You still have to manually
specify which sections of the code are to be parallelised, because, although [implicit
parallelism](https://wikiless.tiekoetter.com/wiki/Implicit_parallelism?lang=en) is possible with Haskell, there are
significant performance disadvantages to a strategy of parallelising everything, because at what level is the compiler
supposed to parallelise workload? With unrestricted parallelisation, you can easily run into hundreds of thousands or
millions of tasks, which is completely pointless on a machine with 16 or 32 cores. As threads have a certain overhead,
you lose more than you gain as soon as the program becomes substantially larger than a dozen lines of code. That being
said, with referential transparency you eliminate two quintessential categories of parallelisation issues: deadlocks
and race conditions. At least for pure functions, but with
[STMs](https://wiki.haskell.org/Software_transactional_memory) it is possible even for impure functions (I/O) with some
tricks. Haskell is also [very fast](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/ghc-gcc.html),
with the only weakness being algorithms which are best done with in-place mutation, which Haskell currently is unable
to do. Haskell is constantly worked on, however, and it is possible that some version down the line will come with a
compiler so smart it knows when to do in-place mutations for maximum efficiency.

I think it is also worthwhile to read [John Carmack's thoughts on functional
programming](https://cbarrete.com/carmack.html), and [this article](https://www.defmacro.org/2006/06/19/fp.html). I
don't think it's a coincidence that John Carmack, the [genius that made
DOOM](https://www.youtube.com/watch?v=hYMZsMMlubg) possible to run on 1990s hardware, is a strong advocate for
functional programming. It is interesting, considering that object-oriented programming, chiefly  with C++, is [widely
regarded as a natural fit for video
games](https://gamedev.stackexchange.com/questions/14158/how-object-oriented-are-videogames).

## Good versus bad

Are languages like Java and JavaScript all clout and no substance? It might seem like I am giving a one-dimensional
overview here with categorising aforementioned languages as good, which implies that most others are bad. Granted, yes,
imperfections in Python or PHP do not make them one-dimensionally bad. They set out to do a job, and for the most part
they do it well.

I will, however, make a bold claim: **most programming languages are just plain terrible**. All clout and no substance.
Java, JavaScript, Ruby, Scala, and many others are popular without substance to justify their popularity. They have
minimal gains for all the disadvantages they come with. Most of them do not even the job they set out to do all that
well. Java is bloated and incoherent. JavaScript specification is a cognitohazard. Ruby is painfully slow and does
nothing that Python or PHP already don't. Scala is just a band-aid over Java that fundamentally does nothing to address
the utter dumpster fire that is the Java runtime environment. There are other languages I have reviewed, but you get
the idea. When compared to existing languages, I simply do not see the value that justifies the existence of these
languages. Of course, I already outlined the explanation for why the clout exists in the first paragraphs of this
article. However, there are people who genuinely defend these languages as good, or even great, when that is factually
incorrect. Everyone is correct in saying that Java, JavaScript, Ruby, and Scala are popular languages, but conflating
that with quality is completely irrational. Quality and popularity of a language, as already briefly explained, do not
go hand in hand at all. Cursory review of histories of all the languages mentioned by name in this article demonstrates
this unambiguously. I do not admonish people who have to deal with these terrible languages as part of the professional
career. If Java development pays, that is fine, but defence of Java as a quality language is inexcusable. I think even
suggesting such things is sign of software engineering incompetence, and fundamental misunderstanding of how computers
work.

Although this might seem like a fatalistic assessment of the state of programming languages, I was unable to come to
any other conclusion.
