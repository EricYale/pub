# Voting

## Definitions
- $m$ candidates/choices
- $n$ voters
- Voter $i$ has a preference list over $[m]$, which is denoted by $\gt_i$
- A **voting rule** is a function from votes (preference lists) to candidates. $$f(\vec\prec) = j \in [m]$$

## Examples of Voting Systems
### Plurality
Selects the candidate with the most first-place votes.

### Borda Rule
Each candidate gives 3 points to their 1st choice, 2 points to their 2nd choice, etc. The candidate with the most points wins.

### Instant Runoff Voting
```
let R: remaining candidates
R = [m]

while |R| > 1:
    Remove from R the candidate with the smallest # of 1st place votes
    Remove R from all candidates' preference lists
```
### Copeland
Match up each pair $(a, b)$ of candidates, and the winner gets 1 point. (Winner decided by how many candidates prefer $a$ to $b$.) Output the candidate with the most points.

### Dictatorship
Pick a voter, they decide.

## Properties of Voting Rules
- **Unanimity**: if everyone has candidate _x_ as their first choice, then _x_ wins.
- **Monotonicity**: moving a candidate up on your preference list should never result in them no longer winning; moving a candidate down should never result in them winning when they were previously losing.
- **Anonymity**: the ordering of the voters is not important.
- **Incentive compatibility**: a voter should not be able to misrepresent their preference list to gain something.

|Voting system|Unanimous|Monotonic|Anonymous|Incentive compatibility|
|--|--|--|--|--|
|Plurality|✅|✅|✅|❌|
|Borda|✅|✅|❌|❌|
|IRV|✅|❌|✅|❌|
|Copeland|✅|✅|❌|❌|
Dictatorship|✅|✅|❌|✅|

## Arrow, Gibbard–Satterthwaite Theorem
"When $m>2$, only dictatorship is unanimous _and_ incentive compatible."

"When $m>2$, there is no voting rule that is unanimous, anonymous, _and_ incentive compatible."
