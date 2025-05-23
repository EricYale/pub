# Data Structures

## ArrayLists
- Insertion: $O(n)$
- Removal: $O(n)$
- Searching: $O(n)$
- Append: ArrayLists must be resized if they go over capacity, so appending to the end is $O(n)$; but, $O(1)$ amortized

## LinkedLists
- Insertion at index: $O(n)$
- Removal at index: $O(n)$
- Searching: $O(n)$
- Append: $O(1)$

## Sorted Arrays
- Think of each element as having a key; higher key means later in sort order

**Operations**
- Search: $O(\log{n})$
- Min/max: $O(1)$
- Predecessor/successor (find neighbor values): $O(1)$
- In-order traversal: $O(n)$
- Select (return the $i$ th order statistic): $O(1)$
- Rank (of a key): $O(\log{n})$
- Insert: $O(n)$
- Delete: $O(n)$

## Binary Search Trees
_h_ is the height of the tree

- Search: $O(h)$
- Min/max: $O(h)$
- Predecessor/successor (find neighbor values): $O(h)$
- In-order traversal: $O(n)$
- Select (return the $i$ th order statistic): $O(h)$
- Rank (of a key): $O(h)$
- Insert: $O(h)$
- Delete: $O(h)$

**Properties**
- Every key in _v_'s left subtree has a smaller key than _v_
- Every key in _v_'s right subtree has a larger key than _v_

### AVL Trees
- AVL Trees keep the tree balanced, so that $h \le O(\log{n})$

## Heaps
- Heap is filled from top to bottom, then left to right

**Operations**
- Find minimum: $O(1)$
- Find and remove minimum (bubble down): $O(\log{n})$
- Insert: $O(\log{n})$
- Heapify: $O(n)$ if we use an array heap
    - But still $O(n\log{n})$ to remove each element, i.e. for heap sort

**Implementation**
- Heap can be implemented as a tree with pointers
- Heap can be implemented as an array
