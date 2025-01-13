# Sorting and Complexity

## Sorting algorithms

### Selection sort
```c
void sort(int list[], int size)
{
    for (int i = 0; i < size; i++)
    {
        int min_idx = i;
        for (int j = i+1; j < size; j++)
        {
            if (list[j] < list[min_idx])
            {
                min_idx = j;
            }
        }
        int tmp = list[min_idx];
        list[min_idx] = list[i];
        list[i] = tmp;
    }
}
```

### Insertion sort
```c
void sort(int list[], int size)
{
    for (int i = 1; i < size; i++)
    {
        int cur = list[i];
        int j;
        for (j = i-1; j >= 0 && list[j] > cur; j--)
        {
            list[j+1] = list[j];
        }
        list[j+1] = cur;
    }
}
```

## Algorithmic complexity

Big O coarsely represents the rate of growth of an algorithm. It is the asymptotic upper bound of the complexity of f(x) as x → ∞.

> For example, `5n^2 = O(n^3)`, but the better answer is `5n^2 = O(n^2)`

Big Ω, on the other hand, is the asymptotic lower bound of f.

Θ means f is bounded both above and below asymptotically by the same function. If f(n) = O(g(n)) and f(n) = Ω(g(n)) then f(n) = Θ(g(n)).

"Best," "worst," and "average" case scenarios mean the complexity given the best/worst/average input of a fixed _n_. For example, in a linear search algorithm, giving an array of size _n_ with the desired element in the first vs. last position.

You can ignore constants, coefficients, and non-dominant terms (only include the term with the highest degree).

### Recurrence Relations
Ex.

```c
void foo(int n)
{
    if (n<=0)return;
    printf("It's me! Hi!");
    foo (n/2);
}
```

```
T(n)    = T(n/2) + c
        = T(n/(2^2))
        = T(n/(2^k)) + ck
        = T(1) + c*log(n)
        = 1 + c*log(n)
```
