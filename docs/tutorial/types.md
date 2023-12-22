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

### Type Arithmetic

Maize supports a few standard types in its standard library.
None of these actually exist in the language by default; see above.


You can create types:
```haskell
X = type X
```

You can create sum types (unions):
```haskell
Z = X | Y
```

You can create product types (tuples):
```haskell
Z = X & Y
```

You can emulate generics:
```haskell
Map key value = type Map where
    empty :: Self

    get :: key -> Self -> value
    put :: key -> value -> Self -> Self

    keys :: Self -> List key
```

Some more examples:
```haskell
IntKeyedMap value = Map Int value

IntValuedMap key = Map key Int
```
