# Predicate Logic
- In Predicate Logic, the atomic elements are **predicates** applied to sequences of **arguments**

## Models
- A **model** of predicate logic is a pair $\langle D, I\rangle$:
    - $D$ is a set of things—a "universe" of which we're speaking
    - $I$ is an interpretation of the symbols in the predicate statement—values for the things in $D$

## Non-logical constants
- $[[\alpha]]^M = I(\alpha)$

## Predications
- Predications ask if something is in a set.
- In other words, $[[\pi(\alpha_1, \alpha_2, \ldots, \alpha_n)]]^M = T$ iff $\langle[[\alpha_1]]^M, \ldots, [[\alpha_n]]^M\rangle \in [[\pi]]^M$

> Ex.
> person = $\{Bob, Alice\}$
> 
> `person(Bob) = T`

## Functionals
- $[[\upsilon(\alpha)]]^M = [[\upsilon]]^M([[\alpha]]^M)$

> Ex. "Sue introduced Bill to Anna"
> 
> `introduced(s, b, a)`

- Predicates can also work as function symbols

> Ex. "If Nate's wife's mom called, Nate is happy"
>
> `called(momOf(wifeOf(n))) --> happy(n)`
