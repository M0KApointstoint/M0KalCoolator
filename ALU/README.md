# Arithmetic Logic Unit (ALU)

**I strongly recommend you first check the ALU `learning` bit:**

```bash
$ cd ../learning/arithmetic_logic_unit/
$ ls -l
```

**I again recommend what I just recommended above if you did not take my**
**recommendation!**

**Abstract ALU scheme:**

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
- 001 (0x1): AND - Bitwise AND, A & B
- 010 (0x2): SUB - Basic subtraction, A - B
- 011 (0x3): NOT - One's complement, bitwise invert B, ~B
- 100 (0x4): XOR - Bitwise XOR, A ^ B
- 101 (0x5): OR  - Bitwise OR, A | B
- 110 (0x6): SHL - Logical left shift on B, B << 1
- 111 (0x7): SHR - Logical right shift on B, B >> 1
```

**Abstract 1-bit ALU chunk from the 8-bit ALU scheme:**

```text
                  Opcode
A0 ───┐           │ │ │
      ▼           ▼ ▼ ▼
   ┌──────┐    ┌───────────┐
   │ ADD0 │───▶│000        │
   ├──────┤    │           │
   │ AND0 │───▶│001        │
   ├──────┤    │           │
   │ SUB0 │───▶│010        │
   ├──────┤    │           │
   │ NOT0 │───▶│011  8 : 1 │
   ├──────┤    │      MUX  │───▶ Result0
   │ XOR0 │───▶│100        │
   ├──────┤    │           │
   │ OR0  │───▶│101        │
   ├──────┤    │           │
   │ SHL0 │───▶│110        │
   ├──────┤    │           │
   │ SHR0 │───▶│111        │
   └──────┘    └───────────┘
      ▲
B0 ───┘
```

*The subtract bit does not appear above but it is taken into account.*

**Subtract bit:**

```text
Subtract bit = Opcode1 * !Opcode0
```

**ALU Flags:**

```text
- Carry flag   : (CF) - The result generated a carry
- Zero flag    : (ZF) - The result is zero
- Negative flag: (SF) - The result is negative (with sign bit on)
- Overflow flag: (OF) - The result generated an overflow
```

