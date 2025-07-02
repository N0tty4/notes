```C
.global _start
_start:

```
- .global makes the `_start` label visible outside the program for the linker.
- Names a certain location in memory
- a label is like a function name, represent a certain area in memory
# how to exit
```asm
.global _start

.section .text
_start:
	mov r7, #0x1
	mov r0, #0x2A
	swi, 0 // is used for interrupt the program
```
- we need to use a special register called `r7` used for syscall.
- `r0` is used for specify the code
- `swi` is used for exit form the program
# Operand commands
## add
```asm
.global _start

.section .text
_start:
	mov r0, #0x4
	mov r2, #0x2
	add r1, r0, #0x3
	add r1, r0, r2
```
- use the form `ADD{s}<c> <Rd>, <Rn>, #<const>`
- in this case we can sum a number with a register and put the value inside another register.
- we can also add 2 register and store the value inside another register
## sub
```asm
.global _start

.section .text
_start:
	mov r0, #0x4
	mov r2, #0x2

	sub r1, r0, r2
```

- use the form `SUB<c> <Rd>, <Rn>, <Rm>`
- is like add
## mul
```asm
.global _start
_start:
	mov r0, #0x4
	mov r2, #0x2
	mult r1, r0, r2
```
- use the form `mul r1, r0, r2`
- can be used only with registers.
# CPSR 
- means (current program status register)
- the `{s}` means that this operator can change this value
# LDR STR

- means Load Register and Store Register is used for load a register, because is the only way in arm assembly
## LDR
carica la un dato dalla memoria in un registro
```asm
.global _start

.text
_start:
    mov r7, #0x4
    mov r0, #0x1
    ldr r1, [var1]
    mov r2, #0x2
    swi 0

    mov r7, #0x1
    mov r0, #0x0
    swi 0

.data
var1: .ascii "5\n"

```
## STR
is used for store from register to memory
```asm
.global _start

.text
_start:
	ldr r0, =var1
	ldr r1, [r0]

	mov r2, #3
	ldr r3, =var2
	str r2, [r3]

.data
var1: .word 5
var2: .word 6
```
- first we need to 
# subroutine vs label
## label
- una label è un identificatore che rappresenta un indirizzo in memoria.
- permette accesso specifica posizione
```asm
.data
	hello: .asciz "hello world\n" 
	hello_end:
```
- in questo caso `hello:` indica solo la posizione di h
- `hello_end:` rappresenta la memoria del carattere subito dopo.
- non eseguono operazioni, sono punti nella memoria.
## subroutine
- blocco di codice che esegue una specifica azione
- può essere chiamata in ogni parte del codice
- possono essere chiamata usando:
	- `lb` (branch with link) salva indirizzo di ritorno nel registro
	- `lr` (link registri)
	- `bx` (branch and exchange) serve per trasferire il controllo all'indirizzo memorizzato in un registro (`lr`) in questo caso.
