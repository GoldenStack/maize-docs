---
sidebar_position: 4
---

# Examples

```haskell title="Hello, world!"
main = "Hello, world!"
```

```haskell title="Hello, ten times"
main = intercalate "\n" $ replicate 10 "Hello"
```

```haskell title="Sum of even squares"
total = sum $ filter even $ map (^ 2) (0..100)
```

```haskell title="2d point type"
Point = data Point of
    x :: Int
    y :: Int
```

```haskell title="Map creation"
map = Map of
    "name" = "Maize"
    "iq" = -26
```

```haskell title="FizzBuzz"
fizzBuzz i
    | m 3 && m 5 = "FizzBuzz"
    | m 3 = "Fizz"
    | m 5 = "Buzz"
    | otherwise = show i
    where
        m value = i % value == 0
```

```haskell title="Closest point in a list to another point"
closest point = minBy $ comparing (distance point)
```