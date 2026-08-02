# Arithmetic Logic Unit (ALU)

**I really recommend you first check the ALU `learning` bit:**

```bash
$ cd ../learning/arithmetic_logic_unit/
$ ls -l
```

**ALU scheme:**

```text
         ALU Opcode
          (3 bits)
             │
             ▼
          ┌─────┐
   A ───▶ │     │
(8 bits)  │     │
          │ ALU │ ───▶ Result
   B ───▶ │     │     (8 bits)
(8 bits)  │     │
          └─────┘
             │
             ▼
           Flags
         (4 flags)
```

**ALU Opcodes:**

```text
- 000 (0x0): ADD - Basic addition, A + B
- 001 (0x1): SUB - Basic subtraction, A - B
- 010 (0x2): AND - BASIC bitwise AND, A & B
- 011 (0x3): OR  - Basic bitwise OR, A | B
- 100 (0x4): XOR - Basic bitwise XOR, A ^ B
- 101 (0x5): NOT - One's complement, bitwise invert A, ~A
- 110 (0x6): SHL - Logical left shift on A, A << 1
- 111 (0x7): SHR - Logical right shift on A, A >> 1
```

**ALU Flags:**

```text
- Carry flag   : (CF) - The result generated a carry
- Zero flag    : (ZF) - The result is zero
- Negative flag: (SF) - The result is negative (with sign bit on)
- Overflow flag: (OF) - The result generated an overflow
```

