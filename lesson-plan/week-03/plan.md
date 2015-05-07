# Week Three: A Few Special Forms

## Table of Contents
1. `let`
  - Nested `define`
  - `let` like `define`, except when it isn't
2. `let*`
3. `lambda`
4. `case-lambda`

## `let`
### Nested `define`
You can nest `define` statements within procedures:
```racket
(define (foo arg)
  (define x 5)
  (define y (+ arg x)
  (write y))

(foo 1) ;=> 6
```

### `let` is like `define`, except when it isn't
`let` is like `define` in many ways. You define a variable and bind some value to it.
The major difference is that `let` creates a new scope for the variables, whereas
`define` adds the variables to the same scope.

You may also define several in a row, based on the outer scope.

```racket
(define (func arg)
  (let ([foo (+1 arg)] ; Uses procedure's scope
        [bar (* 9 arg)])
    bar))
```

Note that the bindings in a `let` expression only last until the `let`'s closing parenthesis

## `let*`
`let*` behaves `let`, but with a new scope created after every binding. This allows
later bindings to use earlier ones in their definition.

```racket
(define (func arg)
  (let* ([foo (+1 arg)]   ; Uses procedure's scope
         [bar (* 9 foo)]) ; Depends on foo
    bar))
```

Here is a little example taken from taken from [Stack Overflow](http://stackoverflow.com/a/16530812/3353734)
```racket
(let ((x 2))
  (let ((x 3) (y x))
    (write y)))
;;=> 2

(let ((x 2))
  (let* ((x 3) (y x))
    (write y)))
;;=> 3
```

## `lambda`
`lambda`s (`λ`s) are very common in functional programming. They allow you to define
procedures as you need them, within other functions. They have the form `(lambda [arg1 arg2 ...] (calculations here))`

```racket
(map (lambda [x] (* x 2)) '[1 2 3])
;;=> '[2 4 6]

(map (λ [x] (+ x 1) '[1 2 3])
;;=> '[2 3 4]
```

## `case-lambda`
`case-lambda` allows us to look at the arguments, and run a different procedure based on the context

Modified from the [Racket docs](http://docs.racket-lang.org/reference/lambda.html#%28form._%28%28quote._~23~25kernel%29._case-lambda%29%29):
```racket
(let ([f (case-lambda
            [() 10]
            [(x) x]
            [(x y) (list y x)]
            [r r])]))

(f) ;=> 10
(f 1) ;=> 1
(f 1 2) ;=> '[2 1]
(f 1 2 3) ;=> '[1 2 3]
```
