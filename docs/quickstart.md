---
sidebar_position: 2
---

# Quickstart

```haskell
-- Comments in Maize start with two dashes.

-- You declare your file
module Main where

-- Hello, world!
main = "Hello, world!"

-- You can also do this:
main = print "Hello, world!"
-- But it's heavily discouraged, because it makes thinking of
-- the program as a single function much more complicated.

-- There are integers and floats
x = 3
y = 2.1

-- You declare types with "name :: type" like so:
z :: Float
z = 3.5

-- Math is what you'd expect
five = 3 + 2
six = 3 * 2
one = 3 - 2
threeHalves = 3 / 2

-- Except ^ (caret) is for exponentiation, not XOR like other languages.
eight = 2^3


-- Booleans are just constants.
isFalse = True && False
isTrue = False || True

isFalse = not True
isTrue = 1 == 2


-- String work like normal Haskell:
helloWorld = "Hello," ++ " " ++ "World!"
-- A string is just a list of characters, so:
name :: List Char
name = ['M', 'a', 'i', 'z', 'e'] -- Lists can be created with the [] operator

-- A list over type M is an ordered collection of M.
numbers :: List Int
numbers = [1, 2, 3, 4, 5]

-- This is just syntax sugar for list concatenation:
numbers = 1 : 2 : 3 : 4 : 5 : [] -- [] is the empty list constant

-- You can also use the .. operator - the range operator
numbers = 1..5

-- Use the !! operator to access an element of a list.
four = numbers !! 3 -- Maize uses zero-based indexing

-- Maize, like Haskell, supports infinite lists:
ints :: List Int
ints = 1..

-- Using Maize's dependent typing, you can have constrained lists:
positiveInts :: List Int where (>0)
positiveInts = 1.. -- Works!

compileError :: List Int where (>0)
compileError = [0, 1] -- Type error: Expected 'Int where (>0)'; found 'Int'


-- Tuples can be created with the , operator:
intBool :: Int, Bool
-- In most cases, you should add parentheses around the tuple
-- to help indicate that it is, in fact, a tuple.
intBool = (3, False) -- But "3, false" without parentheses still works

three = fst intBool -- First element of intBool
false = snd intBool -- Second element of intBool


-- If you don't know what to put in a function, you can add ???
unknown = ???
-- The compiler will tell you what type it needs to be!


-- Calling functions, known as 'function application', is done with
-- the function name on the left, and arguments on the right.
-- Functions do not use any parentheses.
-- There is no difference between a value and a zero-argument function.

add a b = a + b
seventeen = add 5 12

-- The type of "add" here is actually "Int -> Int -> Int".
-- This is equivalent to "Int -> (Int -> Int)".
-- If you look at the type, you can see that, when you call it with two integers
-- consecutively, you get an integer.
-- This is because Maizes uses currying; all multiple-parameter functions are
-- simply functions that return other functions.

-- This means you can also partially apply all functions:
plusFive :: Int -> Int
plusFive = add 5
-- plusFive ends up as a function similar to this:
plusFive = \b -> 5 + b
-- This is because we only gave one argument to the add function, and now to
-- return a value it needs a second argument.


-- Maize uses the idea of mixfix operators from Agda.
-- If expressions are simply a function:
if_then_else_ :: Bool -> a -> a -> a
-- The underscores indicate that arguments would go there.
-- For example:

red = if True then "red" else "blue"
-- Similar to partial application, you don't actually have to follow the rules
-- of mixfix operators; you can call it like a normal function.
blue = if_then_else_ True "red" "blue"
```