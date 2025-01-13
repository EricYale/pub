# Overflow Attacks
- Lack of boundary checking in C/C++ leads to vulnerability to buffer overflow attacks

## Stack Overflow
- Data is copied without checking boundaries
    - `gets`, `strcpy`, `strcat`, `sprintf`, `vsprintf`, `scanf` are all vulnerable
- Data "overflows" a pre-allocated buffer, and overwrites parts of the frame like the return address
- Allows attacker to jump to user-defined code, e.g. a shellcode that gives the attacker a shell

## Defenses
### Memory Safe Languages
- Dynamic memory management (Java, Python, C#)
- Compile time checks (Rust)

### Stack Canaries
- Insert a value into a stack frame right before the return address
- Random value chosen when program is loaded
- Verify on return from a function that the value was not modified

### Shadow Stack
- Create a second stack that stores only the return addresses
- Function prologue and epilogue push/pop return address to the shadow stack
- On return, check that the return addresses match

### Non-executable stack/heap
- Do not allow executing instructions from stack/heap
- May interfere with certain programs like JIT compilation
- Can be defeated with return-oriented programming (ROP)

#### Return-Oriented Programming (ROP)
- Instead of injecting shellcode, attacker chains together existing code snippets
- For example, if attacker needs a gadget to dump data, they can look for code that matches
```asm
mov %eax, (%edx)
ret
```
- Then they can call this instruction to dump data. They then use more gadgets to do other tasks
- Chained together, these gadgets can perform arbitrary tasks

##### Defenses against ROP
- Address Space Layout Randomization (ASLR)
    - Implemented by the OS
    - Randomize the base address of the stack, heap, and libraries
    - Makes it harder to find gadgets
- PIE: Position Independent Executable
    - Code is compiled so that binaries are freely relocatable throughout address space
    - This is necessary for ASLR to work
