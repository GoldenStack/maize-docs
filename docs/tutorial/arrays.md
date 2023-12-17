---
sidebar_position: 3
description: 'Maize supports lists.'
---

### Lists

A list is a collection of items.

To create a list, you can put items between square brackets, separated with
commas.

You can also create a list by prepending items to a list.
Here, we create an empty list, and prepend 3, 2, and 1, to it.
```haskell
list = [1, 2, 3]
sameList = 1 : 2 : 3 : [] -- same thing as the previous list
```

You can use `!!` to get an item from a list.
```haskell
two = list !! 1
```

The `!!` operator could cause a runtime error, so you can just use `!` instead.

This will return `Just` the value, or `Nothing` if the index is invalid
```haskell
justTwo = list ! 1 -- Just 2
nothing = list ! 3 -- Nothing
```
