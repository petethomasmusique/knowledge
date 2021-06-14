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
which means, the function head expects an input of a list of type anything, and an output of a single instance of the anything.

## Types and Classes

### Part 1
[Video link](https://learning.edx.org/course/course-v1:DelftX+FP101x+3T2015/block-v1:DelftX+FP101x+3T2015+type@sequential+block@340eb2baa2854836ad02ac9593723a4f/block-v1:DelftX+FP101x+3T2015+type@vertical+block@8e521cc07ce34602aac19b701750101d_)

Types are names for collections of values with related properties. 

Types errors occur when we apply a function to a type that it does not expect.

The goal of static typing is that these get caught at compile time - before the programme runs. Dynamically typed is where types are checked at runtime, when your programme is running.

Expression types in Haskell are written:
```
e :: t
```

`::` reads as 'has type of'. Every well formed expression has a type. These can be automatically calculated at compile time using a process called 'type inference'.
```
:t -- calculate type of expression
```
#### Base types
```
Bool
Char
String -- list of Chars. You could say it's not really a base type
Int -- fixed precision
Integer -- none fixed precision. You can calculate computationally expensive values and they won't overflow, as they would with Int. 
Float
```
#### Generic / Polymorphic type
List -- sequence of values of all same type. Length is unrestricted.
Tuple -- sequence of values of different types. The type contains the length however.
```
(False,'a') :: (Bool,Char)
```
Above the type is a tuple of Bool and Char. For more clarification here, compare to:
```
[False,True] :: [Bool]
```
The type of tuple specifies that it must have two items, of type Bool,Char - the lenght is part of the type. The type list of Bool does not specify the lenght, which is arbitrary.

List - Type restricted, length arbitrary
Tuple - Type unrestricted, length restricted

### Part 2
[Video link](https://learning.edx.org/course/course-v1:DelftX+FP101x+3T2015/block-v1:DelftX+FP101x+3T2015+type@sequential+block@340eb2baa2854836ad02ac9593723a4f/block-v1:DelftX+FP101x+3T2015+type@vertical+block@b19f80c097794f43b57a4c00e9cff3a2)

#### Function Types
A function is a mapping from values of one type to values of another type.

In general
```
t1 -> t2
```
A function that takes `t` of type 1 and maps it to `t` of type 2.

This would is written in the syntax below when expressing the type of a function
```
add :: (Int,Int) -> Int
add (x,y) = x+y
```
The top line is the type and bottom line is the definition.
Add has a type of tuple containing two integers, with an output of a single integer.

```
zeroto :: Int -> [Int]
zeroto n = [0..n]
```
Zeroto expects an Int and outputs a list of Ints.

Multiple arguments are possible because Haskell will return a function, which is then applied to the next argument!!! So, we wouldn't really write `add` as above with the sole argument being a tuple. Instead, we'd write it
```
add :: Int -> (Int -> Int)
add x y = x+y
```
Read, add expects an Int and returns a function that expects an integer and returns an integer. Which all sounds like a long way of saying - accepts two arguments. But I'm sure it's significance will reveal itself to me over time. This is called currying.

Because this is so common the parentheses are often dropped, which is why one sees the rather confusing
```
add :: Int -> Int -> Int
```
Where you can't differentiate between the input arguments and output. But that is because they're all inputs with a final output, as we're not thinking in terms of a single function that accepts multiple arguments, rather, a function that accepts an argument, that returns a function that accepts an argument... etc.

Haskell B. Curry is the person who invented this. Haskell is named after him.
```
mult :: Int -> (Int -> (Int -> Int))
mult x y z = x*y*z
```
Parentheses in the type go from right to left. Arrows associates from left to right

Why curried functions useful? Well! This seems to be the basis for being able to do functional programming. 
```
take 5 :: [Int] -> [Int]
```
Because `take` returns a function, we can 'partially apply' it the integer 5, which returns another function. Otherwise, `take` would be closed. Presumably, this is why we can just chain functions together in tidal.

Syntax in Haskell is optimized to be able to express curried functions in a lightweight way.

### Part 3
[Chapter Link](https://learning.edx.org/course/course-v1:DelftX+FP101x+3T2015/block-v1:DelftX+FP101x+3T2015+type@sequential+block@340eb2baa2854836ad02ac9593723a4f/block-v1:DelftX+FP101x+3T2015+type@vertical+block@bfd75b7fd29f40d1a8c0123f12f9e07f)

#### Type classes and polymorphic functions
Polymorphic functions are those that are not defined by types but are defined using type variables. Here's a simple example:
```
length :: [a] -> Int
```
Reads as, the function `length` has the type of - a list of type `a` (anything) that returns type integer.

In this example, `Int` is a concrete type - it starts with a capital letter - whereas `a` is a type variable.

#### Overloaded functions
Overloaded functions in Haskell are those where it's type contains one of more class constraints. 

For example, take the function `sum` - where we expect to input a list of numbers and get back the sum of the items. This would be inappropriate
```
sum :: [a] -> a
```
Because, that would mean that it could accept a list of tuples or characters. Instead, we write:
```
sum :: Num a => [a] -> a
```
Which reads as, takes a list of type `a` where `a` is of type `Num` and returns `a`. Now why could we not write:
```
sum :: [Num] -> Num
```
? Hopefully that will become clear... Ah, yes. So, `Num` is not a type but a type class - so it allows all types that are part of the Num type class. This is rather like implementing an interface in OOP.

Haskell has several type classes, and you can also define your own. For example:
```
Num -- numeric types
Eq -- equality types
Ord -- Ordered types
```
Each type can obviously be part of numerous type classes. 

Some example of where type classes are in use:
```
(+) :: Num a => a -> a -> a
```
The addition function expects type `a` where `a` implements the Num type class. It returns a function which expects type `a` which finally returns a value of type `a`.

```
(==) :: Eq a => a -> a -> Bool
```
Equality expects type `a` where `a` implements the Eq type class. It compares two `a`s and returns a value of type `Bool`.

```
(<) :: Ord a => a -> a -> Bool
```
Less than expects type `a` where `a` implements the Orderable type class. It compares the two `a`s and returns a value of type `Bool`.

## 3 Defining Functions

### Part 1
[Chapter Link](https://learning.edx.org/course/course-v1:DelftX+FP101x+3T2015/block-v1:DelftX+FP101x+3T2015+type@sequential+block@cc6cc5b19e8d41ce81d2f570c488b6ce/block-v1:DelftX+FP101x+3T2015+type@vertical+block@983486d2b7be49af91dc7ec5b84ce9dd)

#### Conditional Expressions
Written in Haskell as:
```
abs :: Int -> Int
abs n = if > 0 then n else -n
```
Abs is a funcion that expects an Int and returns an Int. It asks, if n is greater than 0, return n, otherwise, return negative n.

Since conditionals are expressions rather than statements, you always have to have a if, then and else part. These can be nested too:
```
signum :: Int -> Int
signum n = if n < 0 then -1 else
            if n == 0 then 0 else 1
```

However, because Haskell users like brevity, they don't tend to use conditional expression - favouring instead guarded equations. So, if your function definition begins immediately with a conditional expression, you might want to consider using a guarded equation. The syntax for it is:
```
abs | n > 0 = n
    | otherwise -n
```
This becomes even more useful when you have nested conditional:
```
signum n | n < 0 = -1
         | n == 0 = 0
         | otherwise 1
```

#### Pattern matching
For example,
```
not :: Bool -> Bool
not False = True
not True = False
```

In a more complex example,
```
(&&) :: Bool -> Bool -> Bool
True && True = True
True && False = False
False && True = False
False && False = False
```
Because only one of these cases is true we can collapse this pattern matching down into a much simpler form.
```
True && True = True
_ && _ = False
```
The '_' placeholder is used frequently in Haskell to denote a variable that I don't care about.

However, this is still inefficient because you are asking the compiler to evaluate both sides of the pattern to come up with it's answer. And, because Haskell is a lazy language and we want to do as little compiling as we can, we can write it thus:
```
True && b = b
False && _ = False
```
So, if the first arg is True, bother evaluating the second, and return the second. If the first argument is False, it doesn't matter what the second argument is, the answer will be false

#### List patterns
`[1,2,3,4]` is just syntatic sugar for `1:(2:(3:(4:[])))`. The `:`s are called 'cons' and mean, add an element to the start of a list. Whilst we wouldn't write a list in this way in the usual flow of code, when we're doing pattern matching on lists we might use it. For example,
```
head :: [a] -> a
head (x:_) = x
```
Or
```
tail :: [a] -> [a]
tail (_:xs) = xs
```

### Part 2
[Chapter link](https://learning.edx.org/course/course-v1:DelftX+FP101x+3T2015/block-v1:DelftX+FP101x+3T2015+type@sequential+block@cc6cc5b19e8d41ce81d2f570c488b6ce/block-v1:DelftX+FP101x+3T2015+type@vertical+block@e7f0db6732624d5db3f58143ecc865d1)
