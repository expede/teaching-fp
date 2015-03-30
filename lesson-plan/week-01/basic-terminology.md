# Basic Terminology

## Data Structures
### Lists
A common functional data structure
- Basically an array without an index

## Side Effects
### Side effect
Any change in the world caused by your code
- Reassign a variable
- Print to the terminal
- Fire the missiles

### Pure
No side effects

### Impure
With side effects

### Referencial Transparency
With no side effects, functions can be substituted with their return values
- They are 100% equivalent (see equivalence below)

### Immutability
Once something is defined, it cannot be changed
- You "define" immutabile things
- You "assign" and "reassign" mutable things
- Immutability is "pure", becuase it never changes

### Referential Tranparency
With no side effects, calculated values can be substituted for the functions,
  with no change to program behaviour
- Think about the caching!

## Evaluation
### S-expression
"Symbolic expression"
- Note "expression", like in math

Looks like this: `(+ (- 1 10) (* 8 42))`

### Prefix notation ("Polish notation", or "PN")
- Infix: `1 + 1`
- Prefix: `+ 1 1`, or `add 1 1`
- Postfix: `1 1 +`, or `1 1 add`

### Reduction
Simplify an expression by solving all (or part) of it
- ex. `1 + 2 = 3` reduces `1 + 2` to `3`

### Equivalence
If, when fully reduced, both values are the same

### Identity
A particular thing, not just its value
- "That one"

### Equivalence vs Reduction
`1 + 1 = 2`
- "One plus one is equal to 2"
- "One plus one reduces to two"

`2 = 1 + 1`
- "Two equals one plus one"
- **NB:** This is not reduction!

`1 + 1 = 42 - 40`
- "One plus one is equal to forty-two minus forty"
- **NB:** This is not reduction!

`1 + 1 + 1 = 2 + 1`
- This **is** reduction

## Laziness
### Lazy
Functions are only called when another function needs something from them
- If a function returns many values, pause once the needed number of values are returned
  - When more are needed, continue
- Generally a language feature

### Strict
When you call a function, it finishes calculating _all_ of its values,
  whether they're needed or not