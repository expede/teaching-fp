# Topics to Cover
- Who the hell am I? (Background, day job, etc)
  - Who the hell are you?
  - I *will* forget your names
    - It doesn't mean that I don't care. They simply don't stick.
  - PLEASE ask questions
    - I'm oblivious to what is easy vs hard at this point
    - Want to get good at teaching the material to make more FPers. Mwahahahahaaaa
    - Who has expereince with which languages? Get a read of the room.
  - Who was here for last month's FP talk?
  - Disclaimer: examples aren't particularly tight Haskell. Designed for a beginner audience to be easier to follow.
- Why Haskell?
  - Has _all the functional things_!
- First-class functions
  - defn
    - Either take or return a function (ideally both)
  - Partial Application
    - Get a new function back with one of its arguments frozen
  - Currying
    - Automagic PFA
- Pure Functions
  - Referential transparency
    - Easy to reason about
    - Easy to test
    - Break up calculations without problem
      - Especially when combined with PFA under the hood
    - Threadsafe
  - Memoization
- Recursion
  - Manage scope in a pure setting
- Strict vs Lazy Evaluation
- Type Systems
  - Help focus on the
  - Can prevent an entire class of error
    - No more `nil for nilClass`!
- Idioms
  - `map`, `fold`, `filter` and `scan`
  - Composition
    - Bottom-up vs top-down


# The Basics
## Quick Access to an editor
- Register at [FP Complete](https://www.fpcomplete.com/auth/login)
- Make a new [empty project](https://www.fpcomplete.com/new-project) (left column at the top)

## Install on your system
Either [Haskell Platform Installer](https://www.haskell.org/platform/), or `brew install ghc cabal-install` (if on OS X)

## Hello World & Echo
```haskell
-- Hello World
main = putStrLn "Hello, World!"
```
```haskell
-- Echo
main = do
  putStrLn "> "
  input <- getLine
  putStrLn ("echo: " ++ input)
```
```haskell
-- Haskell REPL
ghci
```


## Summing a range

### Imperative:
```javascript
var myArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

function sum(array) {
  var total = 0;
  for(i = 0; i < array.length; i++) {
    total += i;
  }

  return sum;
}

sum(myArray);
```
- So many pointers! Means lots of complex (nested) state.
- Verbose
- Inelegant

### Functional: Manual
```haskell
myList = [1..10]

sum [] = 0
sum (x:xs) = x + sum xs

-- Expansion:
sum myList
1 + sum [2..10]
1 + 2 + sum [3..10]
...
1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10 + 0
```
- List vs array
  - No index, head, tail, etc
- Pattern matching
- Recursion
- Ask them why we need the `sum []` pattern to round out the recursion


### Functional: Idiomatic
```haskell
list = [1..10]

sum = foldl' (+) 0

-- Equivalent to:
sum x = foldl' (+) 0 x
```
- Explain what `foldl'` does
- Partial application
  - Exmplain tail recursion & memoization
- Ask them why don't I need a `sum []` case handled here?
- Could this be done in parallel for very long lists? (Hint: yes. Ask them how. Hint: chunk the list)



# Type System
```haskell
myList :: [Int]
myList = [1..10]

sum :: [Int] -> Int
sum = foldl' (+) 0

sumMap :: (Int -> Int) -> [Int] -> Int
sumMap = sum . map
-- sumMap f list = sum (map f list)

-- Example usage:
sumMap sqrt [1..100] -- | 22.4682781862041
```
- Type signatures
  - Notice how everything lines up nicely?!
- For the version with implied argments, how does the type signature make it clearer?
- Composition

## Polymorphism
```haskell
-- Not a graet implementation, but gets the job done
take :: Int -> [a] -> [a]
take 0 _      = []
take n (x:xs) = x ++ take (n - 1) xs
```
- Can define your own types very easily!
  - `data PrimaryColour = Red | Blue | Yellow`
  - `data Maybe a = Just a | Nothing`
- Walk them through the recursion
- Explain the currying
- Explain holes (underscore)
- What happens with `take -9 _`?
  - What _should_ happen?
- Show them Hoogle for search by type
  - Examples:
    - `[a] -> Int` (`length`)
    - `(a -> b) -> [a] -> [b]` (`map`)
  - GHCi and HLint can be very expressive with `:t`


================================
Where you may start to lose them
================================

# Evaluation Strategies
Going to do sum the first `n` numbers from zero, ascending

```haskell
-- Strict:
sumCount' :: Int -> Int -> Int
sumCount' n max = foldl' (+) 0 $! [1..max]

-- Lazy:
sumCount :: Int -> Int
sumCount = (foldl (+) 0) . take
-- sumCount' n = foldl (+) 0 (take n [1..])

-- Happy Mix:
sumCount'' :: Int -> Int
sumCount'' n = foldl' (+) 0 (take n [1..])
```
- Composition
- Partial application
- Strictness
  - Advantages
    - Pretty much what imperative programmers are used to
    - Easy to reason about
    - `foldl'` accumulates strictly, thus tail recursion == memory savings
  - Disadvantages
    - `$! [1..max]` could suck up memory if `max` is very large
- Laziness
  - Advantages
    - `take n [1..]` only generates the elements that it needs *as foldl asks for them*
  - Disadvantages
    - Expansion of lazy `foldl` can use tons of memory/stack
- Mix!
  - Best of both!
    - `foldl'` will fully evaluate each cycle, and store the result
    - `take n [1..]` will generate only what's asked for per cycle


# Eliminating `Nil` with `Maybe`
```haskell
data Maybe a = Just a | Nothing

-- Unsafe (remember `sqrt`?):
sumSqrt :: [Int] -> Double
sumSqrt list = sum (map sqrt list)
-- sumSqrt [1,2,3] = 4.146264369941973
-- sumSqrt [1,0,-1] = ERROR: `sqrt (-1)` DOES NOT COMPUTE!

-- Safe, but I'm also being SUPER VERBOSE
safeSqrt :: Int -> Maybe Double
safeSqrt x = if x < 0
               then Nothing
               else sqrt x

safeAdd :: Maybe Double -> Maybe Double -> Maybe Double
safeAdd (Just x) (Just y) = Just (x + y)
safeAdd _        _        = Nothing

safeSumSqrt :: [Int] -> Maybe Double
safeSumSqrt list = foldl' safeReduce 0.0 list
  where safeReduce acc x = safeAdd acc (safeSqrt x)
```
- Nothing can signify failed computation, among other things
  - "Allows" (ie: forces) you to explicitely handle the `Nothing` case
  - No more exception control flow
  - Because of laziness, will generally just bail on the first Nothing (depending on circumstance)
- Sometimes, `[]` is a nonsensical case, or
- Entirely possible to do this in other languages (ie: not a language feature, just math)
  - Not idiomatic in those languages, though :P

# Workshop Exercises
In any language, do the following in a functional style:

1. Sum every second element of a list
2. Write an `evenFilter :: [Int] -> [Int]` function
3. Write a general `filter :: [a] -> [a]` function, for some arbitrary criterea
4. Sum all even numbers in a list
5. Implement `map` from scratch
6. Sum the squares of the first `n` Fibonacci numbers
7. Write `safeTake` (explicitely handle negative counts)