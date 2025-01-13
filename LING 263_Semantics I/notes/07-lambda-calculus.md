# Lambda Calculus

## Motivation
- In first-order logic, there is no way to express incomplete parts of sentences, like "every linguist" or "loves pizza."
- So, you can use lambda calculus to express these incomplete parts.

## Notation
- Lambdas are anonymous functions, and can be called with parentheses, called Beta Reduction
$$
(\lambda x.x^2 + 4)(10) = (x^2 + 4)[x := 10]\\
= 10^2 + 4\\
= 104
$$

```
λx.licked(x, b)(a) = licked(a, b)
```

- Lambda arguments can be expressions too:

```
(λf.f(8))(λx.x+5) =
(f(8))(f := λx.x+5) =
(λx.x+5)(8) =
13
```

## Types

- Lambda functions' types can be notated using angle brackets:

$$
(\lambda x.x+5) : \langle\R, \R\rangle\\
(\lambda f.f(8)) : \langle\langle\R, \R\rangle, \R\rangle
$$

- Special types
    - `e`: entities
    - `t`: truth values (booleans)

```
λx.licked(a, x) : <e, t>
λx.λy.licked(x, y) : <e, <e, t>>
```
