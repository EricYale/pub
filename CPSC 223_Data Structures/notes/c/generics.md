# Generics

To make utility functions that deal with pointers type-agnostic, you can use `void*` type parameters.

## Memcpy

```c
void *memcpy(void *dest, const void *src, size_t n);
```

```c
void swap(void* ptr1, void* ptr2, size_t bytes) {
    // This dynamic array is not good practice
    // TODO: replace with malloc
    char temp[bytes];
    memcpy(temp, ptr1, bytes);
    memcpy(ptr1, ptr2, bytes);
    memcpy(ptr2, temp, bytes);
}
```

## Function pointers
Let's say we have to compare two generic items for a sort function. How can we genericize this compare function?

We can have a pointer to the _text_ block in memory, where the function implementation lives.

```c
// return type (*)(function pointer name)(parameter type list)
bool (*)(compare_fn)(void *, void *)
```

```c
void bubble_sort_int(
    void *arr,
    int n,
    int elem_size_bytes,
    bool (*compare_fn)(void *a, void *b)
) {
    // ...
    if (compare_fn(prev_elem, curr_elem)) {
        // ...
    }
}

bool greater_than(void* ptr1, void* ptr2) {
    // Cast to int
    int* num1ptr = (int*)ptr1;
    int* num2ptr = (int*)ptr2;
    return *num1ptr > *num2ptr;
}

bubble_sort_int(myArr, 5, size_of(int), greater_than);
```

You can put function pointers in structs, so your object can know how to sort/compare/etc itself.