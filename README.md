# Teaching Functional Programming
These are currently my working notes on how to best teach FP

I am by no means an expert in teaching this material! However, most current
materials are "okay" _at best_. There seems to be an increase in people
interested in FP, but many get scared off at the word "functor" or unfamiliar
syntax (ie: not from the C-family).

## Goal
1. Don't scare off newcomers
2. Help popularize FP by helping people teach effectively

## Strategy
- Keep it practical
- Use a flexible language ([Racket](http://racket-lang.org)) so that you don't
need to switch syntax for different concepts
- Progressive
  - Start similar to the student's background (ex. compare to Java)
- Less magic is *literally* demystifying
  - Reimplement common patterns to show how things work
    - `map`, `fold` (left and right), `scan` and `filter` from scratch
  - Compare to imperative language strategy
    - Loops vs recursion

## Contributing
1. Fork the repo
2. Write your post
3. Submit a pull request

## Have Suggestions?
[Submit an issue](https://github.com/expede/teaching-fp/issues/new)!

## Emoji tags for commits, PRs and comments
| Meaning                         | Symbol              | Markdown              |
|---------------------------------|---------------------|----------------------:|
| Idea                            | :bulb:              | `:bulb:`              |
| Approval                        | :+1:                | `:+1:`                |
| Improving code format/structure | :art:               | `:art:`               |
| Improving performance           | :racehorse:         | `:racehorse:`         |
| Plugging memory leaks           | :non-potable_water: | `:non-potable_water:` |
| Writing docs                    | :memo:              | `:memo:`              |
| Bug Fix                         | :bug:               | `:bug:`               |
| Removing code or files          | :fire:              | `:fire:`              |
| Fixing CI build                 | :green_heart:       | `:green_heart:`       |
| Adding tests                    | :white_check_mark:  | `:white_check_mark:`  |
| Security fix                    | :lock:              | `:lock:`              |
| Upgrading dependencies          | :arrow_up:          | `:arrow_up:`          |
| Downgrading dependencies        | :arrow_down:        | `:arrow_down:`        |
| Fix linter warning              | :shirt:             | `:shirt:`             |
