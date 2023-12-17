---
sidebar_position: 1
description: 'The only native type in Maize are functions.'
---

# Types

The native types in Maize are:
- Functions

That's it.

As the lambda calculus is a compile target, it doesn't make sense to have
primitives like integers and floats.

They still exist in Maize; they're just defined by the compiler, with optional
optimizations that are part of the implementation detail.

You can call functions by putting the arguments after the name.
```haskell
-- Define a function that doubles a number
f x = x * 2

-- Call the function with the number four, returning 8.
result = f 4
```

