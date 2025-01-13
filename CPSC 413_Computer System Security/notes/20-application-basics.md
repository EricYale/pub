# Application Security Basics

## Compilation
- Compilers turn code into architecture-specific assembly
- Linker combines binary object with libraries
    - Executable format for Linux: ELF (Executable and Linkable Format)

## Binary and Assembly
- Register conventions
    - Accumulator: `eax`
    - Pointer to data: `ebx`
    - Loop counter: `ecx`
    - I/O operations: `edx`
- Special purpose registers
    - Stack pointer: `esp`
    - Frame pointer: `ebp`
    - Instruction pointer: `eip`

> Caution: AT&T vs Intel syntax
> - AT&T: `mnemonic source, destination`
> - Intel: `mnemonic destination, source`

- Calling convention
    - Caller:
        - Pushes arguments onto stack (left to right)
        - Pushes address of instruction after call
    - Callee:
        - Pushes previous frame pointer onto stack
        - Creates space on stack for local varaibles
        - Ensures that stack is consistent on return
        - Returns value in `eax`
