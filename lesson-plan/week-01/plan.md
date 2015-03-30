# Week One

## Table of Contents
1. Value Proposition
2. Basic Terminology
3. Referential Transparency
4. Reduction
  - i. Graph reduction
  - ii. Evaluation Order
      - Normal Order
      - Applicative Order

## Value Proposition
- _Will_ improve your imperative code
- Expose you to new ideas, think about things differently
- Concurrency & parallelism made easy! Well, _easier_...
- Often shorter clear, clean, concise code
- The dream of Object Orientation successfully realized in a different form
  - Code reuse
  - Cleanliness

## Basic Termonology
- Lists
  - A common functional data structure
  - Basically an array without an index

- Side effect
  - Any change in the world caused by your code
    - Reassign a variable
    - Print to the terminal
    - Fire the missiles
- Purity
  - No side effects
- Referencial Transparency
  - With no side effects, functions can be substituted with their return values
  - They are 100% equivalent (see equivalence below)

- Immutability
  - Once something is defined, it cannot be changes
  - You "define" immutabile things
  - You "assign" and "reassign" mutable things

- S-expression
  - "Symbolic expression"
  - Note "expression", like in math
  - Prefix notation ("Polish notation", or "PN")
    - Infix: `1 + 1`
    - Prefix: `+ 1 1`, or `add 1 1`
    - Postfix: `1 1 +`, or `1 1 add`

- Reduction
  - Simplify an expression by solving a part of it
  - ex. `1 + 2 = 3` reduces `1 + 2` to `3`
- Equivalence
  - If, when fully reduced, both values are the same
- Identity
  - A particular thing, not just its value
  - "That one"

- Laziness
  - Generally a language feature
  - Functions are only called when another function needs something from them
  - If a function returns many values, pause once the needed number of values are returned
    - When more are needed, continue
- Strictness
  - When you call a function, it finishes calculating _all_ of its input, no matter what

## Referential Tranparency
- With no side effects, calculated values can be substituted for

## Equivalence vs Reduction
`1 + 1 = 2`
- "One plus one is equal to 2"
- "One plus one reduces to two"

`2 = 1 + 1`
- "Two equals one plus one"
- **NB:** This is not reduction!

`1 + 1 = 42 - 40`
- "One plus one is equal to forty-two minus forty"
- **NB:** This is not reduction!
