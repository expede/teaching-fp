# Exercises
## `deep-map`
Using what you have learned and a little ingenuity, write a procedure that `map`s
over trees (ie: nested lists)
- Turns empty lists to `0`
- Converts an letter to `20`
- Doubles all numbers

Example usage:
```racket
(deep-map foo '[[] 1 2 [3 4 5] [[6 7] [8 9] #\a]])
;;=> '[0 2 4 [6 8 10] [[12 14] [16 18] 20]]
```
