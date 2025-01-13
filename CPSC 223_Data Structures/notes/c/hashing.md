# Hashing

## Hash maps

- A hash map is an array of pointers to linked lists
- Array indexed by hashes; to access an item, go to the spot in the array of `hash % table_size`, and traverse the list until you find your item
- Load factor: `# things in table ÷ # slots in table`
    - The table should be recreated with a a larger array if the load factor reaches a critical point

## Hash functions

### Strings
- Weighted sum of characters, with coefficient increasing exponentially
    - `sum((a^i) * str[i])`
    - Works best if `a` and table size are **relatively prime**

## Open addressing
- To avoid using linked lists, you can store duplicates in other slots in the table.
- When there is a collision, you use a **probe sequence** which tells you which cell to check next.
    - Very common probe sequence is to just skip _i_ entries  to the next (or for _i_ = 1, go to the next entry).
        - `h(k, i) = (h(k, 0) + i) mod m`
        - Can generate up to m probe sequences
    - However, linear probing tends to create clusters, so we can add a constant times the ssquare of the iteration:
        - `h(k, i) = (h(k, 0) + ci + di^2) mod m`
        - Need to use number theory (primes?) to make sure this hits all slots
        - Can generate up to m probe sequences
    - Double hashing: add another hash to find the next slot
        - `h(k, i) = (h_1(k) + i*h_2(k)) mod m`
        - Can generate up to m^2 probe sequences—better since there are more permutations so less likely to cluster!
- To access:
    1. Go to the slot in the hash
    2. Compare to the value
    3. If not your value, go to the next slot in the probe sequence
    4. If the slot is empty, item is not in table
    5. Repeat
