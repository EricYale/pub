# Greedy Algorithms
- A greedy algorithm is one where a simple decision is repeatedly made, resulting in the optimal solution.

## Example: Max Non-Overlapping Intervals
- Given a list of intervals (start time $s$ and finish time $f$), choose a subset so that you have the maximum number of intervals that don't overlap.
- Solution: greedily choose the next interval with the earliest end time that doesn't have a conflict

### Correctness
- "Greedy stays ahead"
    - If our algorithm has failed, an optimal solution has at least one more item in it

#### Lemma: The _i_-th element in our solution will never have a later finish time than the _i_-th element of any other list

i.e. $\forall i: S[i].f \le T[i].f$ for our solution S and any other selection of intervals T

**Base case** ($i=1$): per the greedy algorithm, our first element is the element with the earliest finish time. There is no other element with an earlier finish time

**Inductive step**

Assume our inductive hypothesis is true, i.e. $S[k].f \le T[k].f$. Prove $S[k+1].f \le T[k+1].f$

Since $S[k].f \le T[k].f$ (by inductive hypothesis) and $T[k].f \le T[k+1].f$, we know that $T[k+1]$ has no overlaps with any $S[1 \dots k]$.

So, we know that we would've picked $T[k+1]$ instead if it had an earlier finish time.

#### Proof that the algorithm is optimal
Suppose there is a better solution $T$ with at least one more element, i.e. $\lvert T \rvert \ge \lvert S \rvert + 1$

By the above lemma, we know that for all _k_, $S[k].f \le T[k].f$.

In particular, we can say $S\left[\lvert S \rvert\right].f \le T\left[\lvert S \rvert\right].f \le T\left[\lvert S \rvert + 1\right].s$

But, the equation above just said that $T[\lvert S \rvert + 1]$ doesn't overlap with any of our elements! So our algorithm would have added it or some other element, which is a contradiction.

## Example: Minimize Maximum Lateness of Jobs
- Given a list of jobs ($j_i$), how long they take ($t_i$), and their deadlines ($d_i$)...
- Minimize the max amount of time any one job is late

### Algorithm
- Repeatedly do the job with the earliest deadline first

### Correctness

#### Base Case: Two Jobs
- Take two jobs, $j_1$ and $j_2$
- Assume $d_1 \le d_2$ (swap the jobs if not true)
- If we do $j_1$ first, like our algoritm suggests:
    - Lateness of $j_1$ is $t_1 - d_1$ (just the time it takes to complete job 1)
    - Lateness of $j_2$ is $t_1 + t_2 - d_2$ (since we do $j_1$ first)
- If we do $j_2$ first, contrary to our algorithm:
    - Lateness of $j_1$ is $t_1 + t_2 - d_1$
    - Lateness of $j_2$ is $t_2 - d_2$
- Compare the two cases
    - The lateness of $j_1$ in the second cases _dominates_ both latenesses in the first case (by simple arithmetic)
    - So, doing job 2 first can never be better

#### Greedy Exchange Argument
- If we can prove that swapping two entries will never make the result worse, then we can argue that sorting the list by that property is optimal
- Use similar logic as above
- We pretend we run bubble sort on it; and prove that swapping two elements will never make the result worse
