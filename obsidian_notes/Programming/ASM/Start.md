Is low-level programming language that communicate directly with hardware. Is like human readable version of machine code. For each family of CPU exists different type of assembly.
# syntax of Assembly
has two prevalent syntax: `AT&T` and Intel. Linux uses naturally the `AT&T` syntax
## AT&T syntax
```asm
mov $1, %rax
```
## Intel syntax
```asm
mov rax, 1
```
in both the cases we are assigning the value 1 at the register specified.
# write hello world
it is the code for write hello world in assembly
```asm
.global _start

.section .data
message: .ascii "Hello Baeldung\n"

.section .text
_start:
    mov $1, %rax
    mov $1, %rdi
    mov $message, %rsi
    mov $15, %rdx
    syscall
        
    mov $60, %rax
    mov $0, %rdi
    syscall
```
## dissection of the code
### entry point
```asm
.global _start
```
this directive `_start` specifies the entry point in the program, like the `main()` function in C,
### data section
```asm
.section .data
message: .ascii "Hello world\n"
```
