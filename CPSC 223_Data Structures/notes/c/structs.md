# Structs

```c
struct myStruct {
    int myNum;
    char myChar;
}
struct myStruct x; // with this approach you have to type `struct`

// OR...
typedef struct {
    int myNum;
    char myChar;
} myStruct;
myStruct x;

x.myNum = 10;
x.myChar = 'y';
```

## Opaque structs
By putting the struct implementation in a .c file, you can hide struct fields from direct access. This means you can only modify/get the struct via the associated methods, which enforces the use of getters/setters.

Ex. opaque struct of a list
```c
// list.h

typedef struct list_instance_t list;

// the rest of the list methods like create and destroy
```
```c
// array_list.c

struct list_instance_t {
    size_t length;
    size_t capacity;
    int* array;
};

// the implementation of list methods
```

## Self-referential structs
If you want a struct to contain a property of type itself, you must do this:
```c
typedef struct list_node node;
struct list_node {
    node* next;
};
```
