---
sidebar_position: 3
---

# Features

### Partial Application
Partial application is where you can call a function without all of its
arguments.

For example, here we have a function that adds 5 to any number given to it.
```haskell
add5 = (+) 5
```
We only provide one argument to the `+` operator, meaning that, out of its two
arguments, it only requires one more. This means that the `add5` function above
is essentially equivalent to:
```haskell
add5 b = \b -> 5 + b
```

Partial application is heavily used within Maize code, given that you're usually
writing function combinators.

### Compile Time and Macros
Maize does not have compile time, and it does not have macros.

In fact, there isn't even a distinction between compile time and runtime!
It's completely up to the compiler and/or interpreter to manage that.

You can make functions that generate types, without having to specify anything
related to compile time.

For example, you can make a function that generates a list when run:
```haskell
main type = List type
```
Whenever the `main` function is being evaluated, it will generate a list of the
given type.

Maize doesn't even have generics. As demonstrated above, "generics" in Maize are
simply functions that return new types, similar to Zig's compile time generics.
