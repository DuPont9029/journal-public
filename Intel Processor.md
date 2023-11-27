---
created: 2023-02-24T11:24:51+01:00
modified: 2023-02-24T11:25:05+01:00
---

# Intel Processor

# Intel 8086 microprocessor

![Intel 8086](./8086.png)

## Datasheet

### Sizes

- RAM 1MB
- Address FFFFF(hex) => 00000(hex) 20 bit
- word 16b | 2B => [high byte, low byte]
- register 16b => word es. AX => [AH, AL]
- semi-register 8b => byte es. AX formed by 2 semi-register AH and AL
- segmenti ram 64KB => (codice, dati, stack, extra)

NB: Per indirizzare un byte in memoria si usa un indirizzo a 20 bit ma per indirizzare una word si usa un indirizzo a 16 bit quindi il metodo utilizzato per passare da indirizzo logico a indirizzo fisico è:
$\text{indirizzo logico} \cdot 16 + \text{offset} = \text{indirizzo fisico}$

Esempio:

Facendo un esempio in decimale supponiamo di dover indeizzare 5000 sezioni ma possiamo usare solo 2 posizioni, supponiamo di dover arriare a 2647
le due cifre che usaimo sono 20 ora lo moltiplichiamo per 100 quindi si aggiungono due zeri ed arriviamo a 2000 poi gli sommiamo l'offset che in questo caso è 647

$\text{FFFFF} \cdot 16 + 0 = \text{FFFFF0}$

$\text{FFFFF} \cdot 16 + 15 = \text{FFFFFF}$

Tutto questo viene fatto nel BIU

$\text{indirizzo logico} \cdot 2^4 + \text{offset(SP)}$

Questa operzaione si indica con $\text{CS}:\text{IP}$

### Registers

#### Segment registers

Segment register point to segment start address

NB: **can't be pointed to a semi-register**

**CS** = code segment
**DS** = data segment
**SS** = stack segment
**ES** = extra segment

##### Area stack

Indirizzo contenuto nello $\text{SS}$
L'offset è dato dallo Step Pointer $\text{SP}$

Il metodo utilizzato dall'area stack **LIFO** (Last In First Out)
L'ultimo elemento inserito è il primo ad essere estratto

Le istruzioni che si utilizzano per gestire l'area stack sono:

- PUSH (pusha un elemento [word(2B/16b)] nello stack)
- POP (estrae un elemento [word(2B/16b)] dallo stack)

PUSH(contenuto:word) => inserisce contenuto in SP e decrementa SP di 2 perchè abbiamo inserito una word che è di 2B

POP(destinzanione:word) => estrae contenuto da SP e lo mette in destinazione e incrementa SP di 2 perchè abbiamo estratto una word che è di 2B

Queste sono operazioni ad **un solo operando** quindi non hanno un operando di destinazione che è **implicito** e si trova nell'**SP**

#### General purpose registers

**AX** = accumulator
**BX** = base
**CX** = counter
**DX** = data

#### Index registers

**SI** = source index
**DI** = destination index

#### Pointer registers

**IP** = instruction pointer (not aviabile for developer)
**SP** = stack pointer
**BP** = base pointer

#### Flags

**CF** = carry flag
**ZF** = zero flag
**SF** = sign flag
**OF** = overflow flag

### Instructions

#### MOV

MOV is the instruction used to move data from one register to another. It can also be used to move data from a register to a memory address or vice versa.

```assembly
MOV destination, source
```

#### ADD

ADD is the instruction used to add two numbers. It can be used to add two registers or a register and a memory address.

```assembly
ADD destination, source
```

#### SUB

SUB is the instruction used to subtract two numbers. It can be used to subtract two registers or a register and a memory address.

```assembly
SUB destination, source
```

#### MUL

MUL is the instruction used to multiply two numbers. It can be used to multiply two registers or a register and a memory address.

```assembly
MUL destination, source
```

#### DIV

DIV is the instruction used to divide two numbers. It can be used to divide two registers or a register and a memory address.

```assembly
DIV destination, source
```

#### INC

INC is the instruction used to increment a number. It can be used to increment a register or a memory address.

```assembly
INC destination
```

#### DEC

DEC is the instruction used to decrement a number. It can be used to decrement a register or a memory address.

```assembly
DEC destination
```

#### CMP

CMP is the instruction used to compare two numbers. It can be used to compare two registers or a register and a memory address.

```assembly
CMP destination, source
```

#### JZ

JZ is the instruction used to jump to a specific address if the zero flag is set.

```assembly
JZ address
```

#### JNZ

JNZ is the instruction used to jump to a specific address if the zero flag is not set.

```assembly
JNZ address
```

#### JMP

JMP is the instruction used to jump to a specific address.

```assembly
JMP address
```

#### CALL

CALL is the instruction used to call a subroutine. It pushes the address of the next instruction onto the stack and then jumps to the subroutine.

```assembly
CALL address
```

#### RET

RET is the instruction used to return from a subroutine. It pops the address of the next instruction from the stack and then jumps to that address.

```assembly
RET
```

#### PUSH

PUSH is the instruction used to push a value onto the stack. It can be used to push a register or a memory address onto the stack.

```assembly
PUSH source
```

#### POP

POP is the instruction used to pop a value from the stack. It can be used to pop a register or a memory address from the stack.

```assembly
POP destination
```

#### LOOP

LOOP is the instruction used to loop a specific number of times. It decrements the counter register and then jumps to a specific address if the counter register is not zero.

```assembly
LOOP address
```

#### INT

INT is the instruction used to call an interrupt. It pushes the address of the next instruction onto the stack and then jumps to the interrupt handler.

```assembly
INT number
```

#### HLT

HLT is the instruction used to halt the processor. It stops the processor from executing any more instructions.

```assembly
HLT
```

### Data types

#### Word

A word is a 16-bit data type. It is used to store a single number.

#### Double word

A double word is a 32-bit data type. It is used to store two numbers.

#### String

A string is a sequence of characters. It is used to store text.
