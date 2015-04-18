# Weekly Exercises

## Goal
Get used to the basics of Racket syntax

## Exercise #1
Write a `my-cube` procedure, that satisfies:

```racket
(my-cube 0)   ;; => 0
(my-cube -1)  ;; => -1
(my-cube 2)   ;; => 8
(my-cube 1.5) ;; => 3.375
```

## Exercise #2
Write an `my-even?` procedure, that satisfies:

```racket
(my-even? 0)       ;; => true
(my-even? 99)      ;; => false
(my-even? 42)      ;; => true
(my-even? (* 2 9)) ;; => true
```

## Exercise #3
Write an `compare-num` procedure, that satisfies:

```racket
(compare-num 0 1)         ;; => 'greater
(compare-num 999 -82)     ;; => 'lesser
(compare-num 42 (* 2 21)) ;; => 'equal
```
