---
sidebar_position: 2
description: 'Quickstart (learnxinyminutes-style)'
---

# Quickstart

```haskell

-- Basic file declaration
module Main where

-- Hello, world!
main = "Hello, world!"

-- Comments in Maize start with two dashes, like in Haskell.

-- Place a context on the left and an expression on the right
-- to define a function over a type.

-- Constant declaration with constant expression.
bool = True

-- Constant declaration with type annotation
one :: Nat -- natural number
one = 1

six :: Float
six = 4 * 1.5

-- Except ^ (caret) is for exponentiation, not bitwise XOR like other languages.
eight = 2^3

-- Constant declaration with evaluated (but still constant) expression.
seven = 3 - 4

-- Use ++ for string concatenation. The "String" type is equal to "List Char".
helloWorld :: List Char
helloWorld = "Hello," ++ " " ++ "World!"

-- Declaration with parameter "x" and an evaluated expression (x * 2).
-- The first word (e.g. "double") is the name and the others are parameters.
double x = x * 2

-- Declaration with constant parameter "True" (because it is in scope),
-- two other parameters, and an expression.
if True t f = t
-- The type of "if" here is "Bool -> a -> a -> a".
-- With parentheses, it's "Bool -> (a -> (a -> a))".
-- This means that when you provide a boolean and two values, it returns a
-- resulting value - the same thing as a "normal" pure `if` statement.
-- This is because functions are curried: multiple-parameter functions are
-- simply higher-order functions.

-- You can different function signatures with constant parameters.
double 0 = 0
double n = n * 2

-- Types are first class (taken from Idris documentation):
isSingleton :: Bool -> Type
isSingleton True = Nat
isSingleton False = List Nat

-- Operators work a similar way. Even if they're used as infix you define
. a b c = a $ b c

-- You can even mix constant parameters and operators with constant values.
-- They are used in order, so this example handles 0^0 correctly.
n^0 = 1
0^n = 0
a^b = a * a^(b-1)

-- You can implement these by destructuring, too.
-- Since integers are represented with Peano axioms, you can destructure a
-- variable to calculate its predecessor.
prev (Succ n) = n
-- The function above is actually a partial function: it only applies to the
-- Succ (successor) type, and not the Zero type.
-- This means that it's always invalid to call "prev 0".
-- To make the function complete over the Nat (natural number) type,
-- just define it for 0.
prev Zero = Zero

-- This is a more complicated example. It's an example of codata.
-- This idea works on results of function calls regardless of existing types.
-- This means that this code doesn't even need to rely on any predefined types.
length (pos x y z) = (x^2 + y^2 + z^2)^0.5
-- It defines the length function over the result of a "pos" function called on
-- three parameters, requiring that (a ^ Int) is defined, where x, y, and z are
-- of type "a".

-- You can also implement tuples with codata:
fst (a, b) = a
snd (a, b) = b
-- This defines `fst` (first) of (a, b) to be `a`, the first element.
-- And it defines `snd` (second) of (a, b) to be `b`, the second element.

-- Function signatures work with implicit context. If I define a function with
-- unknown functions called on a parameter, context will be required to actually
-- evaluate the function. For example:
example a = apply a
-- This requires that there exists "apply :: a -> b".
-- If this is called without the function existing,
-- the caller will inherit the implicit context.
example2 a = example a

-- Error: `apply :: a -> b` not defined (originally referenced in `example`)
b = example2 a

-- You can use implicit context with functions like sort.
list = sort [1:2:3] -- List of [1, 2, 3]
 where
    compare = Order.invert . Nat.compare
-- This works because sort requires the function `compare :: a -> a -> Order`
-- Which is Nat -> Nat -> Order in this case, which we define here.

-- This works for more complicated scenarios.
-- Overriding functions (not meant in the object-oriented sense) in sum is bad
-- practice here; you should `foldl 1 (*) [1:2:3]`. This is just an example.
six = sum [1:2:3]
 where
    fold = (*)
    default = 1

-- On the topic of lists, you use the cons (constructor) operator to create
-- lists. The square brackets are unnecessary but they maintain conformity with
-- other popular languages.

-- You can also create a list by prepending items to a list, like so.
-- Empty square brackets [] indicate an empty list.
sameList :: List Nat
sameList = 1 : 2 : 3 : []

-- You can use !! to get an item from a list.
two = sameList !! 1

-- The `!!` operator could cause a runtime error, so you can just use `!` instead.
-- This will return `Just` the value, or `Nothing` if the index is invalid
justTwo = list ! 1 -- Just 2
nothing = list ! 3 -- Nothing

-- You can use the "where" syntax in a more codata-centered manner, too.
-- This returns a point, defining the x and y properties for it.
pos x y = p
 where
    p :: Pos
    x p = x
    y p = y

-- You can partially apply functions.
-- This exists for every function.
add5 = (+) 5 -- Providing only one parameter; typed (Int -> Int)
eight = add5 3

-- You can define lambda functions like in Haskell.
double = \x -> x * 2
-- This is just syntax sugar for function declaration.
double x = x * 2


-- Types

-- As lambda calculus is an intended compile target, Maize does not have any
-- "normal" primitives like integers and floats.
-- These "primitives" still exist, but they're defined in the standard library
-- with optimizations that are part of implementation detail.

-- Normal type creation
X = type X

-- Sum types (unions)
Z = type X | type Y

-- Product types (tuples)
Z = type X & type Y

-- "Generics" (endofunctors over types)
Map key value = type Map of
    empty :: Self

    get :: key -> Self -> value
    put :: key -> value -> Self -> Self

    keys :: Self -> List key

-- Some more examples
IntKeyedMap = Map Int

IntValuedMap = flip Map $ Int


-- If you don't know what to put in a function, you can add ???
unknown = ???
-- The compiler will tell you what type is expected.

```