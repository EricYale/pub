# P vs. NP

## The Class P
- Problems that are solvable in polynomial time

## The Class NP
- Problems for whicch, given a solution, you can verify that solution in polynomial time
- e.g. finding whether a number is composite is hard[*](https://en.wikipedia.org/wiki/AKS_primality_test), but if I show you the factors of a number, you can quickly verify that it's composite
- A verifier, when shown a **certificate** (e.g. the factors in the above example), outputs "good" if it's convinced; "not good" otherwise
- Any problem in P is also in NP. (you just verify by... solving the problem)

## P vs. NP problem
- "Is every problem that's verifiable in polynomial time also solveable in polynomial time?"

## The Class NP-Hard
- For _any_ NP-Hard problem, every NP problem can be reduced to it!
- Thus, if any one NP-Hard problem is found to be in P, P = NP.

### Sidenote: The Class NP-Complete
- An NP-Complete problem is simply an NP-Hard problem that is itself NP.
- Some NP-Hard problems are not NP (i.e. not verifiable), like the Halting Problem.
