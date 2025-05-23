# Hash Tables
- Hash tables can be implemented using a chaining approach or a probing approach, but for this class, we will use chaining
- Hash table performance is dependent on the hashing algorithm, rate of collision, and the load factor

## Runtime

> Assume hash function runs in $O(1)$

- Insertion is $O(1)$ (given we don't have to check for duplicate keys)
- Search and deletion run in $O(n)$, worst-case if everything collides

## Resizing
- A hash table can be resized when it hits a critical **load factor** (items ÷ capacity)

## Hash Functions
- To prevent against adversarial data, a random hash function among a set of possible functions should be picked every time the program is run
