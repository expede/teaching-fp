# Week Two

## Table of Contents
1. Switching to Scheme
2. Lists
3. Linear Recursion
4. `map`

## 1. Switching to Scheme
- This is just here for completeness
- We were using Clojure last week, but are switching for a variety of reasons
  - See [Strategy in the project README](https://github.com/expede/teaching-fp#strategy)

## 2. Lists
"Lists" are analogous to [linked lists](http://en.wikipedia.org/wiki/Linked_list),
but is implemented as a series of nested tuples of the form `(value, (value, (value, ())))`

```racket
;; In Racket, this looks like this:
'()       ; Empty list (no elements)
'(1 . ()) ; Tuple (list) with one element
'(1)      ; Sugary representation
'(1 . 2) ; Full tuple (two elements)

;; Nested tuples to create lists
'(1 . (2))
'(1 . (2 . (3 . ())))

;; Equivalent sugary syntax
'(1 2 3)

;; Function for combining things into tuples
(cons 1 2)      ;=> '(1 . 2)
(cons 1 '(2 3)) ;=> '(1 . (2 3)) ->sugar-> '(1 2 3)

;; Differing types inside is okay
'(1 'a #\b 1/2 4.22)
```

Notice that this is a similar syntax to a normal S-expression, just with a `'`
in front of it. This is useful later in the course. Don't worry about it for now.

- Head or "first" is the value of the outermost tuple
- Tail or "rest" is the nested list (everything but the head)

### Examples
```racket
(define foo '(1 2 3 4.22))

(first foo)        ;=> 1
(rest foo)         ;=> '(2 3 4.22)
(first (rest foo)) ;=> 2
```

### Advantages
- Very simple structure
- Mirrors S-expression structure
- Good for teaching :P
  - Is a simple version of more advanced data structures
  - Can reuse portion of the list immutably (without destroying the original)
    - ex. `(cons 1 (rest list))`

### Disadvantages
- Despite that you want them to be, this is not an array
  - There are array analogs in most languages
  - Finding an element by index requires passing through all of the elements before
  what you're looking for, which is inefficient
    - O(n)

## 3. Linear Recursion
There's a bunch of version of recursion that we'll be looking at later in
the course, but the simplest is running through a list (a recursive structure).

### Example: find length of a list
```racket
(define bar '(#\a 1/8 42))


(define (my-length list)
  ;; Step 1: Find the base case: the empty list '() has a length of 0
  (if (empty? list)
    0
    ;; Step 2: reduce the smallest next part (the head has length of 1)
    (+ 1
      (my-length (rest list))))) ; Recurse: call my-length on the rest of the list

(my-length bar) ;=> 3
```

## 4. `map`
`map` applies a function to each element in a list or tree.
Let's only worry about lists for now ;)

```racket
(define (my-map func list)
  (cons
    (func (first list))
    (my-map func (rest list))))

(define (double num) (* num 2)) ; As example

(my-map double '(1 2 3)) ;=> '(2 4 6)
```
