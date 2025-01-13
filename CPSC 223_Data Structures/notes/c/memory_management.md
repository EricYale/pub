# Memory Management

## Allocation

- **Malloc**: `void *malloc(size_t size)`
  - Allocates _size_ bytes of uninitialized storage (filled with random values)
  - `size_t` is exactly the same as `unsigned long`
  - Ex. to allocate an int: `int* myInt = malloc(sizeof(int))`
- **Calloc**: `void *calloc(size_t num, size_t size)`
  - Allocates memory for an array of _num_ objects of _size_ bytes each
  - Sets all bytes in the allocated storage to zero
  - Ex. to allocate an int array: `int* myIntArr = calloc(10, sizeof(int))`

## Pointers
- Identified by an `*` after the type
- Pointers store the address of a block in memory
- C does not know the size of the pointed-to memory

> You can assign an untyped pointer using `void*` and can be casted to any pointer type, but they are bad practice.

## How much memory
- `sizeof(type)` returns the size in bytes of the object representation of a type
  - Ex. `sizeof(int) == 4` on Unix
  - Ex. `sizeof(char) == 1` on Unix
  - Ex. `sizeof(char*) == 8` on Unix

## Dynamic arrays
- Pointer points to the first entry in the array—`*myArr == myArr[0]`
- Get value of the _n_th entry by either `myArr[n]` or `*(myArr + n)`

## Function calls
- When arguments are passed to functions, their value is copied. (When a pointer is passed, an alias is created.)

## Freeing memory
- `void free(void* myPtr)`: frees the allocated memory of _myPtr_
- The programmer is responsible for keeping track of memory ownership, and freeing the memory when the last owner goes out of scope
- You should document your functions to indicate ownership transfer during parameter passing and function return

## Reallocation
```c
int* newArr = realloc(myArr, newSize * sizeof(int));
// is the same as:
int* newArr = malloc(capacity * sizeof(int));
memcpy(newArr, myArr, capacity * sizeof(int));
free(myArr);
```

## Memory Layout
- Text: code; constant data; function implementations
- Data: initialized global and static variables
- BSS: uninitialized global and static variables
- Heap: dynamic memory (malloc)
- Stack: local variables
