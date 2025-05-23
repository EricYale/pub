# Correctness

## Loop Invariants
- Observation about something that is true _before_ the loop, which stays true _after each iteration_
- true at beginning of loop
- "true at beginning of loop" _implies_ "true at end of loop" (induction)

### Ex. Proving correctness of Linear Search

Linear search:
```
index = 1
while index < n + 1:
    if A[index] == t, return index
    index = index + 1
return -1
```

Naive way:

> Case 1: there is some _j_ such that `A[j] = t`
> - Suppose without loss of generality that _j_ is the **least** integer such that `A[j] = t`
> - When `i == j`...
>     - `A[i] == A[j]`
>     - So, `A[i] == t`
>     - So, return _i_
>     - So, return _j_
> 
> Case 2: there is no _j_ such that `A[j] = t`
> - Proof by contradiction: assume the return is not -1
> - The only other return statement is in the loop
> - But for that return statement to happen, `A[i] == t`; so, `A[i] == t` for some _i_
> - But that contradicts the assumption that there is no _j_ such that `A[j] = t`

Using loop invariants:

- We know that _t_ is not found before _i_, i.e. _t_ is not in `A[1, ..., index - 1]`
    - Correct at the beginning of the loop because `index - 1 == 0`
    - If true at the beginning of iteration, it is true at the end of iteration
        - Let _i_ be the index at the start of iteration
        - Assume _t_ not in `A[1, ..., i - i]`
        - If `A[i] == t`, the end of the loop is not reached
        - If the end of the iteration is reached, `A[i] != t`, so _t_ is not in `A[1, ..., i]`
        - At the end of the loop, `i = index - 1`, so _t_ is not in `A[1, ..., index - 1]`
- Thus, if we return from the loop, we must have found a valid index
- If we finish, due to the loop invariant, _t_ is not in `A[1, ..., index - 1]` = `A[1, ..., n]`
