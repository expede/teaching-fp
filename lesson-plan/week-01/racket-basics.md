# Racket Basics

## Table of Contents
1. Brief History
2. [Situating the language](http://racket-lang.org)
  - [Style guide](http://docs.racket-lang.org/scribble/reference-style.html)

## Racket Overview
- Practical
  - Excellent community
  - Clear (is a Scheme/Lisp)
  - Very clear documentation
  - Language variants specifically for teaching
- A modern Lisp
- Lazy sequences
- Immutable, persistent data structures
- Good REPL: `racket`
  - Exit by typing `(exit)` (including the parentheses)

## Basic Syntax
```racket
;; Every racket file starts with declaring the Racket variant
;; We're just going to use the "normal" one
#lang racket

;; S-expression ("symbolic expression")
(function-name arg-1 arg-2 arg-3 ... arg-n)

;; Note: Each arg can also be an S-expression
;;       (ie: it's a tree)

;; Define a variable
(define name value)

;; Define a procedure ("function")
(define (name var-1 var-2 ... var-n)
  (do-stuff-here))

;; Evaluate a procedure
(print "Hello, World!");; => Hello, World!
```

### Arithmatic
```racket
(+ 1 1)
;; => 2

(- 1 1)
;; => 0

(+ 1 2 3 4 5)
;; => 15

(* 1 2 3 4 5)
;; => 120

(+ (* 2 2) (/ 10 2))
;; => (+ 4 5)
;; => 9
```

### Definitions and Basic Control Flow
```racket
;; Define a variable
(define foo 10)
;; foo
;; => 10

(define (if-else-less-than-ten x y z)
  (if (< x 10)
      y   ;; <~ Do this if x <  10
      z)) ;; <~ Do this if x >= 10

(if-else-less-than-ten 9 "Hello" "Goodbye")
;; => "Hello"

(if-else-less-than-ten 42 "Hello" "Goodbye")
;; => "Goodbye"

(define (response my-string)
  (case my-string
    "Hello"   "How's it going?"
    "Bye"     "Leaving so soon?"
    "Go away" "No!"
    "Huh?")) ; Default
```
