---
sidebar_position: 1
---

# Introduction

## What is Maize?
Maize is a primarily descriptive programming language.

Heavily based on Haskell, Idris, Agda, and the like, it's dependently typed,
portable, and purely functional.

### Central Idea
Maize prioritizes descriptivity. Maize code is intended to act as an accurate
description of your program, helping keep your code clean and maintainable by
separating optimizations from code and by providing exactly enough developer
freedom. 

Simplicity is a large component of descriptivity: simpler and shorter code is
cleaner and more maintainable. Maize stays simple by providing a few very
powerful features, allowing most features that are standard to modern
programming languages, like lists, sum types, and product types, to be
implemented on top, often simply by implementing a new operator. Even booleans
are defined in their own file in the standard library.

## Why Maize?
Maize prioritizes clean, descriptive, and simple code, by helping the
programmer effectively manage the growing complexity of their programs.

You will not find deeply nested classes, strange bugs due to mutability, or
mountains of closing curly brackets in Maize.
Maize does not have any [red or blue functions](https://journal.stuffwithstuff.com/2015/02/01/what-color-is-your-function/).

To prioritize the descriptivity of the language, all Maize code compiles to the
lambda calculus so your programs can truly last forever. Given a format as
simple as the lambda calculus, you could revisit your code 100,000 years later
and it will still function. In many programming languages, this is an
impossible idea. In Maize, this is simply how the development process works.

Maize has relatively little abstraction over the lambda calculus. Although
Maize seems like an incredibly high-level language, this is purely because it
targets the lambda calculus, a simple and more consistent system.

### Why *not* Maize?
Maize is not a general purpose language. Maize is not a multi-paradigm language.

You cannot write drivers in Maize. You cannot write the world's fastest JSON parser in Maize.

Maize is intended to help you write descriptive and declarative code
effectively. Many modern programming languages try to be a jack-of-all-trades,
supporting many different paradigms, and excelling at none of them.

If you want to write a description of your program, and have that code immune
to the oppression of time, you can write it in Maize.
