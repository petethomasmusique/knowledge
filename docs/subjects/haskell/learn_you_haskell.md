# Learn you Haskell for great good
[Book link](http://learnyouahaskell.com)

## Starting out
[Chapter link](http://learnyouahaskell.com/starting-out)

Usual agabreic stuff.

Negative numbers need parenthesis (-3).

`not` negates boolean statement
```
not (True && True)
```
Testing for equality uses `==` or `/=`

`5 == True` won't work as types have to match

`5 + True` won't work for the same reason

### Functions
`5 * 10` is a function! The * part is the function. It is called an infix function because it is sandwiched in between two things. Most functions are prefix functions.

Functions are called by writing its name, then a space then it's parameters/arguments - no parentheses. This is called function application.

`succ 8` an inbuilt function that returns the successor to the parameter.

`min x y` returns the minimum.

`max x y` returns the maximum.

Function application has the highest precedence, so the two statements are equal
```
succ 9 + max 9 10 + 1
(succ 9) + (max 9 10) + 1
```

If a function takes two parameters, you can call it as an infix function by surrounding it by backticks. These are the same:
```
div 90 10
90 `div` 10
```

### Declaring your own functions
Functions can be defined in a similar way to how they are called, with a = after the name and parameters, defining what they do.
```
doubleMe x = x + x 
doubleUs x y = x*2 + y*2
```
You can call functions within functions.
```
doubleUs x y = doubleMe x + doubleMe y
```
This is a common pattern in haskell - making basic patterns that are obviously correct and combining them into more complex ones.

### If statements
The else statement is mandatory
```
doubleSmallNumber x = if x > 100
                        then x
                        else x*2
```                        
Can also be written on one line
```
doubleSmallNumber x = if x > 100 then x else x*2
```
Because else statement is mandatory, always returns something, which makes it an expression

### Variables
`pete = "Pete"` is essentially a function without parameters. we call this a definition. You can do this when evaluating a file.

`let pete = "Pete"` is used when writing it directly into ghci, or perhaps in Tidal

### Lists
Lists are homogenous data structures, you can have a list of strings or integers, but not strings and integers.

Strings are just lists of characters (denoted by '' - as in 'a'). "hello" is syntactic sugar for ['h','e','l','l','o'].

You can concatenate two lists using ++
```
[1,2,3] ++ [1,2,3,4]
```
Caution when concatenating big lists, has to iterate through the first list in its entirety

Instead, consider putting something at the beginning of the list using `:`
```
'A' : " SMALL CAT"
1 : [1,2,3]
```
Obviously, types have to be the same.

To get an element out of a list use !!
```
[1,2,3,4,5] !! 0
```

### List functions
One seems to do a lot with lists in Haskell. So there are lots of useful inbuilt functions to do with lists.
```
head [5,4,3,2,1]  
-- 5
```
```
tail [5,4,3,2,1]  
-- [4,3,2,1]
```
```
last [5,4,3,2,1]
-- 1
```
```
init [5,4,3,2,1]  
--[5,4,3,2]
```

```
length [5,4,3,2,1]
null [1,2,3] - is a list empty
reverse [1,2,3,4,5]
take 3 [5,4,3,2,1] - take number of items from list
drop 3 [8,4,2,1,5,6] - drop number of items from list
maximum [1,2,3]
minimum [1,2,3]
sum [1,2,3]
product [1,2,3]
4 `elem` [3,4,5,6]  or
elem 4 [3,4,5,6]  is element in the list?
```

### Ranges
Create a list from a range
```
[1..20]
['a'..'z']
```
Specify a step
```
[2,4..20]
['a','c'..'z']
```
Go backwards
```
[20,19..0]
```
You can create infinite ranges by not specifying an upper limit. Obviously these aren't calculated until needed as you're computer would fry.
```
[0..]
```
Which allows you to use these to get interesting series
```
take 20 [0,3..]
```
```
take 10 (cycle [1,2,3])
```
```
take 10 (repeat 1) -- or
replicate 10 1
```

### List comprehensions
List comprehensions are used to create lists using more complex functions . They follow the structure 
```
[function | input set, predicate]
```
* function - function you want to apply to the set
* set - original set of numbers that you want to map over
* predicate - the boundaries of your output
For example
```
[x*2 | x <- [1..10], x*2 >= 12]
```
* function - double each number
* set - a range from one to 10
* predicate - only include number where double the input is greater than or equal to 12
Predicates in list comprehensions are good for filtering lists. e.g.
```
[x | x <- [1..10], odd x]
[x | x <- [1..10], even x]
```
```
let someList = [1,4,20,300]
[x | x <- someList, even x]
```

You can draw on multiple lists to make every possible combination
```
[[x, y, z] | x <- [1..10], y <- [11..20], z <- [21..30]]
```
```
[ x*y | x <- [1..10], y <- [10] ]  
```

Then filter it?
```
[[x, y, z] | x <- [1..10], y <- [11..20], z <- [21..30], x+y+z < 40]
[ x*y | x <- [1..10], y <- [10], x*y > 50 ]  
```

### Tuples
Another data structure, storing several values into a single value - you know how many values and the type of values. They don't need to be homogenous, and the size and types define it's own type!

The syntax to use is parentheses. E.g.
```
("Christopher", "Walken", 55)
```

This is a tuple of type triple. You could combine this in a list, but it would have to be with tuples of the same type, as lists contain homogenous data:
```
[("Christopher", "Walken", 55), ("Peter", "Thomas", 37)]
```

## Types and type classes
[Chapter link](http://learnyouahaskell.com/types-and-typeclasses)

Haskell has a static type system, you can't divide a boolean by an integer for example, and these errors will be caught at compile time, not when the programme is running.

Everything in Haskell has a type, but we don't have to declare it. It is inferred.

`:t` followed by anything lets us know its type. This might be useful for comparing what's happening in tidal!!
```
:t "hello world"
-- "hello world" :: [Char]
```
Note the [], so reads as 'has a type of list of characters'

`[Char]` is the same as String

The output is an expression followed by `::` and its type. `::` can be read as 'has type of'.

Functions also have type definitions. Here's a simple one:
```
removeNonUppercase :: [Char] -> [Char]  
```
Or
```
removeNonUppercase :: String -> String  
removeNonUppercase st = [ c | c <- st, c `elem` ['A'..'Z']]  
```

Here's a more complex one:
```
addThree :: Int -> Int -> Int -> Int  
addThree x y z = x + y + z  
```
Note that there's no special distinction between the parameters and the return type, not sure why yet.

If you want to give your function a type but are not sure what it should be, `:t yourFunction` works

### Common types
* `Int` - integer. Is bounded, so there is a min and max it can be / min and max memory it can take up.
* `Integer` - integer. unbounded so use for really big numbers
* `Float` - real floating point, single precision
* `Double` - real floating point, double precision
The two types for the same function would lead to different outputs
```
circumference :: Float -> Float  
circumference :: Double -> Double  
circumference r = 2 * pi * r
```

* `Bool`
* `Char` - denoted by single quotes
