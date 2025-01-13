# C Basics

## Main function
```c
/**
 * argc: argument count
 * argv: array of arguments
   * element 0 is the name of the executable
 */
void main(int argc, char *argv[]) { }
```

## Variables
Primitives in C are limited, such as `int`, `char`, `double`, `float`, `long`, 👉 pointer 👈. Note the absence of `string` and `bool`.

> Tip: Use `#include <stdbool.h>` to define bool type and TRUE and FALSE constants.

## FILE streams
- Definitions: `size_t`, `FILE`, `EOF`, `stdin`, `stdout`, `stderr`
- `printf(const char *fmt, ...)`
- `puts(const char *str)`
- `scanf(const char *fmt, ...)`
- `char *gets(char *str)`
- `int getchar()`

### Format strings
- `%d`, `%i`: decimal integer
  - `%Nd`, `%Ni` (where N is an integer)
- `%s`: string
  - `%Ns`: prints first N characters from string
- `%lf`: long decimal floating point (double)
  - `%N.Mlf` (N and M are integers)
- `%zu`: unsigned size (size_t)

Example:
```c
char* myName = "Eric";
printf("Hello, %s!", myName);
```

A format string with multiple conversion fields delimits those fields with any whitespace, even newlines.
```c
scanf("%d %d %f", &x, &y, &z);
// Ex: 41 51234 3.14
// Ex: 41       51234       3.14"
// will all be read
```

### Reading strings containing whitespace
```c
scanf("%6[^\n]") // Read the first 6 non-newline characters
```

### File I/O
```c
FILE *infile = fopen("in.txt", "r");
  // r - read, w - write, a - append
FILE *outfile = fopen("out.txt", "w");
// use fprintf, fscanf, other functions starting with f
fclose(infile);
fclose(outfile);
```

## Compilation and linking
- When you compile a file, the compiler only knows about the imported headers, not their implementations
- You can compile multiple files and link them, for example `gcc file1.c file2.c`
- But sometimes you don't have access to the source files. You can get around this with object files

### Compiling without linking
```bash
gcc -c file1.c # Compile file1 without linking
gcc -c file2.c # Compile file2 without linking

# file1.o and file2.o will be generated,
# which contain machine instructions, but the
# locations of called imported function bodies
# are left blank

gcc -o executable.out file1.o file2.o
  # Link file1 and file2
```

### Make files
```makefile
target: dependency1 dependency2
  rm foo # your commands here
dependency1:
  touch foo
dependency2:
  echo "hello world" > foo
```

Example simple makefile
```makefile
factorial: factorial.o libfac.o
  gcc -o Factorial factorial.o libfac.o
factorial.o: factorial.c
  gcc -c factorial.c
libfac.o: libfac.c
  gcc -c libfac.c
```


Ultimate makefile
```makefile
CC = gcc
CFLAGS = -std=c17 -Wall -pedantic -g
Factorial: factorial.o libfac.o
  $(CC) $(CFLAGS) -o $@ $^
factorial.o: factorial.c libfac.h
  $(CC) $(CFLAGS) -c $<
libfac.o: libfac.c libfac.h
  $(CC) $(CFLAGS) -c $<
```

> Make knows to automatically generate .o files, so you *could* exclude those rules. It will also add flags from a magic variable named CFLAGS. But then header files won't force a recompilation.

## Arrays
```c
int arr[10];
arr[4] = 5;
```

- You cannot return an array from a function because it will have gone out of scope
- Amount of memory is allocated at compile time, so array size must be a literal

### Strings
Strings in C are null-terminated:
```c
char text[] = "Hello"
// Length of `text`: 6
// text[]: {'H', 'e', 'l', 'l', 'o', '\0'}
```

Character arrays are mutable and on the stack, character pointers are immutable and on the heap