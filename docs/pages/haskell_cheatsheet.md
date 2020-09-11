# Haskell Cheatsheet

## Commands
Load script (useful for loading page of functions)
```
:l myScript
```
Reload
```
:r myScript
```
Get types (of variable, expression, anything really)
```
:t
```

## Functions
Function declaration. Note that a space denotes a function, rather than parentheses in mathematics
```
doubleMe x = x + x
```

## Lists

Concatenate a list
```
[1,2,3,4] ++ [5,6,7]
```
Concat a string (which is just syntactic sugar for a list of characters)
```
"Hello " ++ "World"
```
Add a singleton to the start of a list
```
'H' : "ello World"
```
Or
```
1 : [2,3,4]
```
Get an element out of list by index - if you use this you're still thinking imperatively
```
[1,2,3,4] !! 0
```
You can compare lists using < > <= >=. Does it by lexicographical order
```
[3,2,1] > [2,1,0]
```
Create a list from a range
```
[1..20]
['a'..'z']
```
Specify a step - completes the range in steps between first two 
```
[2,4..20]
['a','c'..'z']
```
Go backwards
```
[20,19..0]
```

### List functions
```
head
tail
last
init
length
null -- is list empty?
reverse
take
drop
maximum
minimum
sum
product
elem
cycle
repeat
replicate
zip -- take two lists and combine into list of pair tuples
```




