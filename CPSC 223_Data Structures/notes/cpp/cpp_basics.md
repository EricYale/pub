# C++ Basics

## Classes

### Constructors
```cpp
class Circle {
public:
    double radius;

    Circle() // Constructor
    {
        radius = 1;
    }
    Circle(double newRadius) // Constructor overload
    {
        radius = newRadius;
    }
};

int main()
{
    Circle circle1; // call default constructor
    Circle circle2(25); // call overload constructor
    Circle* circle3 = new Circle(50); // store on heap
}
```

### Destructors
- If no destructor is provided, the default destructor will deallocate all strings and other variables.
- If you have a reference to another class instance, you have to overload the destructor to make sure proper memory cleanup occurs.
- The default destructor of a pointer is a no-op, but using the delete keyword on a pointer will free it.

```cpp
class Circle {
publlic:
    ~Dog() // Destructor
    {

    }
}
```

## Structs
- By default, struct members are public, but class members are private
- Otherwise, they are exactly the same
- Traditionally, you use a struct when you only have member variables, but a class when there are member methods
