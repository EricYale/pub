# Templates

## Template Functions

You can make generic functions that take in a variety of types using templates.

```cpp
template <typename ElemType>
void printArray(ElemType data[], int length) { /* ... */ }
```

## Template Classes

You can make entire classes generic.

> Note: You cannot separate implementations and declarations into different files for template classes.

```cpp
template <typename ElemType>
class LinkedList
{
public:
    void add(ElemType elem);
private:
    struct Node {
        ElemType data;
        Node* next;
    }
}
```
