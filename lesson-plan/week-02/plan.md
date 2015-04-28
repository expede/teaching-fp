# Week Two

## Table of Contents
1. Switching to Scheme
2. Lists
3.

## 1. Switching to Scheme
- This is just here for completeness
- We were using Clojure last week, but are switching for a variety of reasons
  - See [Racket Overview in `racket-basics.md`](https://github.com/expede/teaching-fp/blob/master/lesson-plan/week-01/racket-basics.md#racket-overview)

## 2. Lists
"Lists" are analogous to [linked lists](http://en.wikipedia.org/wiki/Linked_list),
but is implemented as a series of nested tuples of the form `(value, (value, (value, ())))`

```racket
;; In Racket, this looks like this:
'(1)     ; List with one element
'(1 . 2) ; Normal tuple

;; Nested tuples to create lists
'(1 . (2))
'(1 . (2 . (3)))

;; Equivalent sugary syntax
'(1 2 3)

;; Differing types inside
'(1 'a \b 1/2 4.22)
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

## 3. Simple Recursion

## 4. Maps
