# Week One Terms: Side Effects
## Side effect
Any change in the world caused by your code
- Reassign a variable
- Update a database record
- Print to the terminal
- Fire the missiles

## Impure
With side effects

## Pure
No side effects

### Referencial Transparency
Because you have no side effects, you don't have to worry about updates to
variables by another part of the system, which gets you "referencial transparency"
- Functions can be substituted with their return values
- They are 100% equivalent (see equivalence below)
- Can cache the result of running once and substitute everywhere in the code
  - Don't have to repeatedly compute
- Easy to reason about

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
`1 + 1 =  2`
`1 + 1 -> 2`
- "One plus one is equal to 2"
- "One plus one reduces to two"

`2 = 1 + 1`
- "Two equals one plus one"
- **NB:** This is not reduction!

`1 + 1 = 42 - 40`
- "One plus one is equal to forty-two minus forty"
- **NB:** This is not reduction!

`1 + 1 + 1 -> 2 + 1`
`1 + 1 + 1 =  2 + 1`
- This **is** reduction
