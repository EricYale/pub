# TTCA Incentive Compatibility

## Definitions
- **Incentive compatibility**: "no patient can misreport their preferences to rig a better match for them."
$$M_A\left(p, \left(\vec{\succ}_{-p}\right)\right) \ge_p M_A\left(p, \left(\vec{\succ}_{-p}'\right)\right)$$

## Theorem 4.1. TTCA is Incentive Compatible
Assume there is a patient that has an incentive to misreport his preferences. We will contradict this assumption.

### Definitions for Theorem 4.1

- $N_j$: set of patients matched (removed from the graph) in the $j$th iteration of TTCA
- $p$: the patient with the incentive to misrepresent his preferences
- $\ell$: the iteration of TTCA where $p$ is matched

### Proof
- The options for each patient only get slimmer as the algorithm goes on, so if $p$ were to be any happier, he would need to be matched in steps $1 \dots \ell - 1$.
    - So let's say $p$ gets matched in step $i$, i.e. $p \in N_i$.
- For $p$ to be happier, it would need to be part of a cycle in step $i$. However, this would require that there be an incoming edge to $p$.
- There could never be an incoming edge to $p$ because no one would ever prefer $p$'s favorite (since options only get slimmer, and $p$ gets matched in a later iteration).
- Thus, just by changing his own preferences, $p$ could not create an alternative situation which would be beneficial to him _and_ not detrimental to anyone else.

[[TODO: insert image]]