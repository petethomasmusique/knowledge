# Edx: Intro to Functional Programming 

[Course link](https://courses.edx.org/courses/course-v1:DelftX+FP101x+3T2015/course/)

## Introduction - Part 1

Functional langs provide an elegant framework to write code at a high level of abstraction. We will use Haskell, but they can be applied immediately to use in JS / PHP etc.

A style of programming in which expressions are more important than using statements.

When writing statements, you have have implicit side-effects to the global state and you communicate values via the global state.

When composing using expressions we take multiple expressions that deliver values and compose them into bigger expressions.

Most modern languages now support this style but supporting lambda expressions.

* Statement based

```
var total = 0;
for (var i = 1; i <= 10; i++) {
    total + 1;
}
```

* Expression based

```
sum [1..10]
```

## Introduction - Part 2

* Alonzo Church invented Lambda Calculus. All languages today support these statements.
* John McCarthy in the 1950s invented Lisp - first functional language, but still had imperative features.
* ISWIM first pure func lang. No assignments just pure functions
* FP
* ML - hybrid - introduced type inference and polymorphic types
* Haskell is a lazy language, as opposed to strict. Built on the work of David Turner.
* SASL is the mother of Haskell.
* 1987 - start of Haskell with idea to build standard lang that people could use to experiment. Petri dish for programming language research.

## First Steps - Part 1

Repl - read-eval-print-loop - for executing single lines of code, like a terminal
Ghci to start the repl.
You get the prelude > prompt.
This comes with loads of existing functions, mainly ones that work on lists.

In Haskell, lists are not arrays. Indexing into a list will work it out by traversing across the list in a linear fashion. Which is not very efficient. However, if you are doing some list indexing, ie
```
[1,2,3,4,5] !! 3
```
This means that you’re still in the imperative mindset and there are much better ways to do this.

In mathematics when you apply a function to an argument you use parentheses, and a space means multiply
```
f(a,b) + c d
```
"Apply the function f to a and b, the add the result of c * d"

In Haskell, function application is denoted by whitespace. E.g.
```
f a b + c*d
```
"Apply the function f to a and b, the add the result of c * d"

Function application has higher priority than all other operators
```
f a + b
```
Means apply a to the function f then add b. It does not mean, add a and b together then apply to the function f.

## First Steps - Part 2

Moving beyond simple expressions and loading full scripts.
When using GHC - edit your script in one window then reload the script when you make changes.
To run a script use

```
ghci myscript.hs
```

To reload the same script run
```
:reload
```

If you define functions in the script, e.g.
```
double x = x * x
quadrubpe x = double (double ) 
```
These will become available on the command line

Functions and parameter names must begin with lower case.

Defining a type must start with uppercase.

By convention, list arguments usually have an `s` suffix. For example,
```
xs -- a list of values of type x
ns -- a list of values of type n
nss -- a list of lists
```
By convention, arguments are short, rather than descriptive words. 

Whitespace is significant. Each definition must begin in the the same column:
```
a = 10
b = 20
```
rather than
```
a = 10
 b = 20
```
Or,
```
a = b + c
    where
        b = 1
        c = 2
d = a * 2
```
### Useful GHC commands
```
:load script.hs
:reload
:edit script.hs
:edit
:type expr -- show type of expr
:? -- show all commands
:quit -- exit
```
### Lab
When getting type using `:t` we get responses back such as:
```
:t head "hello"
head "hello" :: Char
```
Which shows the input and the type of the result.

When getting type of a function you can expect something like this:
```
: head
head :: [a] -> a
```
which means, the function head expects an input of a list of type anything, and an output of a single instance of the anything





