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

#### Example: Texture Constants
Texture loading is a common feature throughout programs. Generally, there are two ways of obtaining texture files: statically (embedding them in project files) and dynamic (reading them from known files at runtime).

This is a tricky problem because textures are often extremely large, making them tricky to deal with. Many languages like C force you to have a long array embedded in your source code. This is bad. Rust has a great feature to fix this: the `include_bytes!` macro. This lets you embed bytes from a local file within the game source, solving the problem of static file inclusion.

Or does it? An issue here is that you have to make large code changes when you want to switch between static and dynamic linking.

The solutions that come to mind in Rust are:
- Loading in `main` and passing it around (bad)
- Using OnceCell (good)

The issue with OnceCell is that it requires a significant change in your codebase. It keeps the type of the object the same, which is good, but making rapid code changes demands easy refactorability.

Maize's solution to this is...  your code doesn't know if the texture is being loaded at compile time or runtime. You can write code like this:
```Haskell
menuIcon = png "images/menu.png"
```
And you can effortlessly change whether it's run at compile time or runtime. This is determined by whatever is loading the file.

To elaborate, this is because each file is a function itself. If I have a file that uses imports, the file can still be (mostly) evaluated; it just requires some imports to actually produce results. Take this file:
```Haskell
exampleFunction a = (a ++) ++
```
Extra code at the top is omitted, but it has the type
```Haskell
(a -> a) -> (a -> a)
```
This means you can "compile" this program by just giving it a function. This works with general constants, too. Going back to our previous example:
```Haskell
menuIcon = png "images/menu.png"
```
The `png` function could be provided during compile time, or it could be provided during runtime. In fact, due to the semantics of function provision, different calls of `png` could be run at different times (i.e., compile time or runtime).

This keeps your file as a function and allows you to easily switch runtime vs compile time *without adding any new features*. This texture loading idea just emerges from good, existing features, and can make your code much more refactorable.

