# Weekly Exercises

## Goal
Get used to the basics of Clojure syntax

## Exercise #1
Write a `my-cube` function, that satisfies:

```clojure
(my-cube 0)   ;; => 0
(my-cube -1)  ;; => -1
(my-cube 2)   ;; => 8
(my-cube 1.5) ;; => 3.375
```

## Exercise #2
Write an `my-even?` function in Clojure, that satisfies:

```clojure
(my-even? 0)       ;; => true
(my-even? 99)      ;; => false
(my-even? 42)      ;; => true
(my-even? (* 2 9)) ;; => true
```

## Exercise #3
Write an `compare-num` function, that satisfies:

```clojure
(compare-num 0 1)         ;; => :greater
(compare-num 999 -82)     ;; => :lesser
(compare-num 42 (* 2 21)) ;; => :equal
```