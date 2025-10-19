# Stable Matching

## Definitions
### Two-Sided Matching Markets
A two-sided matching market requires:
- Two sides (men and women, students and universities, etc); here we will use $S$ and $U$ where $$\lvert S \rvert = \lvert U \rvert = n$$
- Every student has a **preference ordering**. The notation $$u_1 \succ_s u_2$$ denotes that student $s$ prefers $u_1$ to $u_2$ .
- Every university also has a preference ordering of students, denoted with the symbol $\succ_u$.

### Matchings
- A set $M \subseteq S \times U$ is a **matching** iff each student and one university appear at most once in $M$
- $M$ is **complete** if each student and each university appear exactly once
- $M(s)$ denotes the university that matched with student $s$; $M(u)$ denotes the student that matched with university $u$
    - If $s$ is unmatched in $M$, then $M(s) = \bot$

### Pareto-Optimality
- A matching is **Pareto-optimal** if there is no other matching such that:
    1. All students are equally happy, if not happier, in the other matching: $$\forall s \in S \mid M'(s) \succeq M(s)$$
    2. There is one student that is strictly happier in the other matching: $$\exists s \in S \mid M'(s) \succ M(s)$$
    3. (Same for universities)

### Stability
- A pair (student, university) is a **blocking pair** if both the student and university prefer each other to their current partners.
- A matching is **stable** if there are no blocking pairs.

## Deferred Acceptance Algorithm
> While there are unmatched students:
>
> Have an arbitrary unmatched student propose to their favorite university to which they have not proposed already.
>
> If the university hasn't tentatively accepted any student yet, or if the university likes the new student better, they tentatively match with the student and un-accept their previous student.

```
M: temporary matching
U_s ≤ U: subset of universities that student s has proposed to

Repeat until M is complete
    s = (arbitrary unmatched student)
    u = favorite school of s in U\U_s
    
    if u is unmatched in M:
        match s to u
    else if s >_u M(u):
        Update the previous match's U_s to include the school it just got unmatched from
        unmatch u from its previous match M(u)
        match s to u
    else
        Do not modify matchings
        U_s = U_s ∪ {u}
```

### Theorem 1.1. The algorithm always outputs a stable matching

#### Lemma 1.1. The algorithm always terminates
- In every iteration, either
    1. The size of the matching has increased
    2. The number of universities some student has already proposed to increased.
- This means the algorithm will always terminate, since `U_s` and `M` have finite sizes.

#### Lemma 1.2. Every school is matched to their favorite student who has proposed so far
- Base case: trivial
- Inductive step: Assume the lemma is true after _t_ proposals. Two cases
    1. If university $u$ is unmatched, it becomes matched with $s$.
    2. If university $u$ is already matched, it swaps its match for $s$ iff it prefers $s$ to $M(u)$. In any case, it remains matched to its favorite student.

#### Corollary 1.1. Every university becomes happier as the algorithm progresses

Obvious from lemma 1.2.

#### Lemma 1.3. All parties are matched at the end of the algorithm
If there were to be an unmatched student $s$, then there is an unmatched school $u$. But, $s$ has proposed to $u$ at some point, so at some point $u$ rejected $s$ for another student. But this cannot happen because of lemma 1.2.

#### Proof of Theorem 1.1
- Goal: prove that there is no blocking pair.
- Assume that there _were_ a blocking pair $(s, u)$.

Two implications of this:
1. $u \succ_s M(s)$: $s$ proposed to $u$ before proposing to $M(s)$ since students propose in descending order of preference
2. $s \succ_u M(u)$: contradiction to Lemma 1.2; student $s$ has proposed to $u$ but was apparently rejected.
