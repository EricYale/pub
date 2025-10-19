# Compatibility Matching
> Optimal kidney exchange (OKE) is an optimization problem faced by programs for kidney paired donations (also called Kidney Exchange Programs). Such programs have large databases of patient-donor pairs, where the donor is willing to donate a kidney in order to help the patient, but cannot do so due to medical incompatibility. The centers try to arrange exchanges between such pairs. For example, the donor in pair A donates to the patient in pair B, the donor in pair B donates to the patient in pair C, and the donor in pair C donates to the patient in pair A. (Wikipedia)

- <span style="color: red;">**Important**: in our simplified scenario, we only concern ourselves with swaps, not cycles of 3 or greater. (Our hospitals can only do 4 operations at one time.)</span>

## Compatibility

- In a compatibility matching scenario, each patient is either compatible to each donor, or not.
- Define graph $K$ as such:
    - Vertices $P$, containing all patients
    - Edge $(p_1, p_2)$ exists if $p_1$ is compatible with $d_2$ AND $p_2$ is compatible with $d_1$
- Goal: match as many patients as possible.

## Kidney Exchange Matching Algorithm (KEM)
- $M$: set of "maximum" matchings, i.e. matchings that match as many patients as possible

```
for i = 1..n:
    Z_i = subset of M_(i - 1) that match i
    if Z_i ≠ 0:
        M_i = Z_i
    else
        M_i = M_(i - 1)
```

> Start with the set of all possible solutions that match the max number of patients. Whittle down those options to only the ones that patient 1 is in. Then, whittle those down to only the ones that patient 2 is in (unless patient 2 has no solutions that they are in). Repeat for all patients.

## Incentive Compatibility
**Why not just pick a random maximum matching?**
We want to make it so that no patient can rig their compatibility list so that they're more likely to get matched.

> Note that we assume that no patient will say they _are_ compatible with a donor they are actually _not_ compatible with...

If patient $i$ tries to report that they _aren't_ compatible, it won't help them get matched. All you're doing by misreporting is shrinking the subset $Z_i$.

## Problems with KEM
1. In rare cases, cycles of length 3 might be possible (instead of just swaps)
2. Computational efficiency?
3. Incentive compatibility for hospitals -- hospitals may prefer internal exchanges, or prioritize their own patients
