# Clojure Basics

## Table of Contents
1. Brief History
2. Situating the language
  i.  Not purely functional
  ii. Lisp-1

## Clojure Overview
- Practical
  - Excellent community
  - Clear (is a Lisp)
  - Good existing resources
  - Awesome frameworks that people can use _now_
- Hickey developed Clojure because he wanted a modern Lisp for
  functional programming, symbiotic with the established Java platform,
  and designed for concurrency [via Wikipedia]
- Lazy sequences
- Java integration (runs on the JVM)
- Immutable, persistent data structures
- Good REPL
  - [Online](http://www.tryclj.com)
  - CLI: `lein repl`

## Basic Syntax
```clojure
;; S-expression ("symbolic expression")
(function-name arg-1 arg-2 arg-3 ... arg-n)

;; Note: Each arg can also be an S-expression
;;      (ie: it's a tree)

;; Define a variable
(def name value)

;; Define a function
(defn name [var-1 var-2 ... var-n]
  do-stuff-here)

;; Call a function
(println "Hello, World!");; => Hello, World!
```

### Arithmatic
```clojure
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
```clojure
(def x 10)
;; x
;; => 10

(defn if-else-less-than-ten [x y z]
  (if (< x 10)
      y   ;; <~ Do this if x <  10
      z)) ;; <~ Do this if x >= 10

(if-else-less-than-ten 9 "Hello" "Goodbye")
;; => "Hello"

(if-else-less-than-ten 42 "Hello" "Goodbye")
;; => "Goodbye"

(defn response [my-string]
  (case my-string
    "Hello"   "How's it going?"
    "Bye"     "Leaving so soon?"
    "Go away" "No!"
    "Huh?")) ;; Default
```