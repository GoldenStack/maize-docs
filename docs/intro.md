---
sidebar_position: 1
---

# Introduction

## What is Maize?
Maize is a dependently typed, portable, purely functional programming language.

It's heavily based on Haskell, Idris, Agda, and the like.

### Central Idea
Maize attempts to generalize modern features of programming languages.
Ubiquitous features like lists, sum types, and product types are all defined as
functions and operators in the standard library. Even booleans are simply
defined in their own file.

Maize also takes inspiration from the functional world, generalizing common
types and ideas; this includes having dedicated types (`Functor`, `Bifunctor`,
`Monad`, `Monoid`, `Foldable`, etc.) for the commonalities of many common data
types and behaviours, managing complexity and code readability.

## Why Maize?
Maize aims to effectively manage complexity whilst also being clean and readable.
You will not find deeply nested classes, strange bugs due to mutability, or
mountains of closing curly brackets in Maize.
Maize does not have any [red or blue functions](https://journal.stuffwithstuff.com/2015/02/01/what-color-is-your-function/).

Maize compiles to simple lambda calculi—including the lambda calculus itself—so
your programs can truly last forever. You could revisit a program 100,000 years
later and, given a format as simple as the lambda calculus, it will still
function. In many programming languages, this is an impossible idea. In Maize,
this is simply how programming works.

### Why *not* Maize?
Maize is not a general purpose language. Maize is not a multi-paradigm language.

You cannot write drivers in Maize. You cannot write the world's fastest JSON parser in Maize.

Maize is intended to do one thing, and do it well. Many modern programming
languages try to be a jack-of-all-trades; they support many paradigms, but excel
at none of them.

If you want to write a specific style of legible code, and have that code immune
to the oppression of time, you can write it in Maize.
